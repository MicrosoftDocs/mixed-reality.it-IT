---
title: Rendering in DirectX
description: Viene illustrato il rendering olografico per la realtà mista di Windows.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, ologrammi, rendering, grafica 3D, HolographicFrame, ciclo di rendering, ciclo di aggiornamento, procedura dettagliata, codice di esempio, Direct3D
ms.openlocfilehash: a781093e0054a986b81a0e284e03076dd018f8c0
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277509"
---
# <a name="rendering-in-directx"></a><span data-ttu-id="4a61a-104">Rendering in DirectX</span><span class="sxs-lookup"><span data-stu-id="4a61a-104">Rendering in DirectX</span></span>

<span data-ttu-id="4a61a-105">La realtà mista di Windows si basa su DirectX per produrre un'esperienza grafica 3D avanzata per gli utenti.</span><span class="sxs-lookup"><span data-stu-id="4a61a-105">Windows Mixed Reality is built on DirectX to produce rich, 3D graphical experiences for users.</span></span> <span data-ttu-id="4a61a-106">L'astrazione del rendering si trova appena sopra DirectX e consente a un motivo dell'app sulla posizione e sull'orientamento di uno o più osservatori di una scena olografica, come previsto dal sistema.</span><span class="sxs-lookup"><span data-stu-id="4a61a-106">The rendering abstraction sits just above DirectX and lets an app reason about the position and orientation of one or more observers of a holographic scene, as predicted by the system.</span></span> <span data-ttu-id="4a61a-107">Lo sviluppatore può quindi individuare i propri ologrammi in relazione a ogni fotocamera, consentendo all'app di eseguire il rendering di questi ologrammi in vari sistemi di coordinate spaziali quando l'utente si sposta.</span><span class="sxs-lookup"><span data-stu-id="4a61a-107">The developer can then locate their holograms relative to each camera, letting the app render these holograms in various spatial coordinate systems as the user moves around.</span></span>

<span data-ttu-id="4a61a-108">Nota: in questa procedura dettagliata viene descritto il rendering olografico in Direct3D 11.</span><span class="sxs-lookup"><span data-stu-id="4a61a-108">Note: This walkthrough describes holographic rendering in Direct3D 11.</span></span> <span data-ttu-id="4a61a-109">Un modello di app per la realtà mista Direct3D 12 Windows viene fornito anche con l'estensione dei modelli di app per realtà mista.</span><span class="sxs-lookup"><span data-stu-id="4a61a-109">A Direct3D 12 Windows Mixed Reality app template is also supplied with the Mixed Reality app templates extension.</span></span>

## <a name="update-for-the-current-frame"></a><span data-ttu-id="4a61a-110">Aggiornamento per il frame corrente</span><span class="sxs-lookup"><span data-stu-id="4a61a-110">Update for the current frame</span></span>

<span data-ttu-id="4a61a-111">Per aggiornare lo stato dell'applicazione per gli ologrammi, una volta per ogni fotogramma l'app:</span><span class="sxs-lookup"><span data-stu-id="4a61a-111">To update the application state for holograms, once per frame the app will:</span></span>
* <span data-ttu-id="4a61a-112">Ottenere un <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> dal sistema di gestione dello schermo.</span><span class="sxs-lookup"><span data-stu-id="4a61a-112">Get a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> from the display management system.</span></span>
* <span data-ttu-id="4a61a-113">Aggiornare la scena con la stima corrente del punto in cui la visualizzazione della fotocamera sarà quando il rendering viene completato.</span><span class="sxs-lookup"><span data-stu-id="4a61a-113">Update the scene with the current prediction of where the camera view will be when render is completed.</span></span> <span data-ttu-id="4a61a-114">Si noti che la scena olografica può contenere più di una fotocamera.</span><span class="sxs-lookup"><span data-stu-id="4a61a-114">Note, there can be more than one camera for the holographic scene.</span></span>

<span data-ttu-id="4a61a-115">Per eseguire il rendering delle visualizzazioni della fotocamera olografica, una volta per ogni fotogramma l'app:</span><span class="sxs-lookup"><span data-stu-id="4a61a-115">To render to holographic camera views, once per frame the app will:</span></span>
* <span data-ttu-id="4a61a-116">Per ogni fotocamera, eseguire il rendering della scena per il frame corrente, usando la visualizzazione della fotocamera e le matrici di proiezione dal sistema.</span><span class="sxs-lookup"><span data-stu-id="4a61a-116">For each camera, render the scene for the current frame, using the camera view and projection matrices from the system.</span></span>

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a><span data-ttu-id="4a61a-117">Creare un nuovo frame olografico e ottenere la relativa stima</span><span class="sxs-lookup"><span data-stu-id="4a61a-117">Create a new holographic frame and get its prediction</span></span>

<span data-ttu-id="4a61a-118">Il <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> contiene informazioni necessarie per l'app per aggiornare ed eseguire il rendering del frame corrente.</span><span class="sxs-lookup"><span data-stu-id="4a61a-118">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> has information that the app needs in order to update and render the current frame.</span></span> <span data-ttu-id="4a61a-119">L'app avvia ogni nuovo frame chiamando il metodo **CreateNextFrame** .</span><span class="sxs-lookup"><span data-stu-id="4a61a-119">The app begins each new frame by calling the **CreateNextFrame** method.</span></span> <span data-ttu-id="4a61a-120">Quando viene chiamato questo metodo, le stime vengono effettuate usando i dati dei sensori più recenti disponibili e incapsulati nell'oggetto **CurrentPrediction** .</span><span class="sxs-lookup"><span data-stu-id="4a61a-120">When this method is called, predictions are made using the latest sensor data available, and encapsulated in **CurrentPrediction** object.</span></span>

<span data-ttu-id="4a61a-121">Per ogni frame sottoposto a rendering è necessario usare un nuovo oggetto frame perché è valido solo per un istante di tempo.</span><span class="sxs-lookup"><span data-stu-id="4a61a-121">A new frame object must be used for each rendered frame as it is only valid for an instant in time.</span></span> <span data-ttu-id="4a61a-122">La proprietà **CurrentPrediction** contiene informazioni come la posizione della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="4a61a-122">The **CurrentPrediction** property contains information such as the camera position.</span></span> <span data-ttu-id="4a61a-123">Le informazioni vengono estrapolate nel momento esatto in cui il frame dovrebbe essere visibile all'utente.</span><span class="sxs-lookup"><span data-stu-id="4a61a-123">The information is extrapolated to the exact moment in time when the frame is expected to be visible to the user.</span></span>

<span data-ttu-id="4a61a-124">Il codice seguente è tratto da **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-124">The following code is excerpted from **AppMain::Update**:</span></span>

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a><span data-ttu-id="4a61a-125">Elaborare gli aggiornamenti della fotocamera</span><span class="sxs-lookup"><span data-stu-id="4a61a-125">Process camera updates</span></span>

<span data-ttu-id="4a61a-126">I buffer indietro possono variare da frame a frame.</span><span class="sxs-lookup"><span data-stu-id="4a61a-126">Back buffers can change from frame to frame.</span></span> <span data-ttu-id="4a61a-127">L'app deve convalidare il buffer nascosto per ogni fotocamera e rilasciare e ricreare le visualizzazioni delle risorse e i buffer di profondità in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="4a61a-127">Your app needs to validate the back buffer for each camera, and release and recreate resource views and depth buffers as needed.</span></span> <span data-ttu-id="4a61a-128">Si noti che il set di pose nella stima è l'elenco autorevole di fotocamere utilizzate nel frame corrente.</span><span class="sxs-lookup"><span data-stu-id="4a61a-128">Notice that the set of poses in the prediction is the authoritative list of cameras being used in the current frame.</span></span> <span data-ttu-id="4a61a-129">In genere, questo elenco viene usato per eseguire l'iterazione sul set di fotocamere.</span><span class="sxs-lookup"><span data-stu-id="4a61a-129">Usually, you use this list to iterate on the set of cameras.</span></span>

<span data-ttu-id="4a61a-130">Da **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-130">From **AppMain::Update**:</span></span>

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

<span data-ttu-id="4a61a-131">Da **DeviceResources:: EnsureCameraResources**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-131">From **DeviceResources::EnsureCameraResources**:</span></span>

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a><span data-ttu-id="4a61a-132">Ottenere il sistema di coordinate da utilizzare come base per il rendering</span><span class="sxs-lookup"><span data-stu-id="4a61a-132">Get the coordinate system to use as a basis for rendering</span></span>

<span data-ttu-id="4a61a-133">La realtà mista di Windows consente all'app di creare vari [sistemi di coordinate](coordinate-systems-in-directx.md) in base alle esigenze, ad esempio il frame di riferimento collegato e il frame di riferimento fisso, che tengono traccia dei percorsi nel mondo fisico.</span><span class="sxs-lookup"><span data-stu-id="4a61a-133">Windows Mixed Reality lets your app create various [coordinate systems](coordinate-systems-in-directx.md) as needed, such as the attached reference frame and the stationary reference frame, that track locations in the physical world.</span></span> <span data-ttu-id="4a61a-134">L'app può quindi usare questi sistemi di coordinate per motivare la posizione in cui eseguire il rendering degli ologrammi per ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="4a61a-134">Your app can then use these coordinate systems to reason about where to render holograms each frame.</span></span> <span data-ttu-id="4a61a-135">Quando si richiedono le coordinate da un'API, viene sempre passato il <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> all'interno del quale si desidera esprimere tali coordinate.</span><span class="sxs-lookup"><span data-stu-id="4a61a-135">When requesting coordinates from an API, you will always pass in the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> within which you want those coordinates to be expressed.</span></span>

<span data-ttu-id="4a61a-136">Da **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-136">From **AppMain::Update**:</span></span>

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

<span data-ttu-id="4a61a-137">Questi sistemi di coordinate possono quindi essere utilizzati per generare matrici di visualizzazione stereo durante il rendering del contenuto nella scena.</span><span class="sxs-lookup"><span data-stu-id="4a61a-137">These coordinate systems can then be used to generate stereo view matrices when rendering the content in your scene.</span></span>

<span data-ttu-id="4a61a-138">Da **CameraResources:: UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-138">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a><span data-ttu-id="4a61a-139">Input di sguardi e movimenti del processo</span><span class="sxs-lookup"><span data-stu-id="4a61a-139">Process gaze and gesture input</span></span>

<span data-ttu-id="4a61a-140">Gli input [sguardo](gaze-in-directx.md) e [mano](hands-and-motion-controllers-in-directx.md) non sono basati sul tempo e pertanto non è necessario aggiornarli nella funzione **StepTimer** .</span><span class="sxs-lookup"><span data-stu-id="4a61a-140">[Gaze](gaze-in-directx.md) and [hand](hands-and-motion-controllers-in-directx.md) input are not time-based and thus do not have to update in the **StepTimer** function.</span></span> <span data-ttu-id="4a61a-141">Tuttavia, questo input è un elemento che l'app deve esaminare per ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="4a61a-141">However this input is something that the app needs to look at each frame.</span></span>

### <a name="process-time-based-updates"></a><span data-ttu-id="4a61a-142">Elaborare gli aggiornamenti basati sul tempo</span><span class="sxs-lookup"><span data-stu-id="4a61a-142">Process time-based updates</span></span>

<span data-ttu-id="4a61a-143">Qualsiasi app per il rendering in tempo reale richiede un modo per elaborare gli aggiornamenti basati sul tempo. viene fornito un modo per eseguire questa operazione nel modello di app olografico di Windows tramite un'implementazione di **StepTimer** .</span><span class="sxs-lookup"><span data-stu-id="4a61a-143">Any real-time rendering app will need some way to process time-based updates; we provide a way to do this in the Windows Holographic app template via a **StepTimer** implementation.</span></span> <span data-ttu-id="4a61a-144">Questo comportamento è simile a quello fornito nel modello di app UWP di DirectX 11, quindi, se si è già esaminato il modello, è necessario avere una certa familiarità.</span><span class="sxs-lookup"><span data-stu-id="4a61a-144">This is similar to the StepTimer provided in the DirectX 11 UWP app template, so if you already have looked at that template you should be on familiar ground.</span></span> <span data-ttu-id="4a61a-145">Questa classe helper di esempio StepTimer è in grado di fornire aggiornamenti fissi per i passaggi temporali, nonché aggiornamenti variabili in fase temporale e la modalità predefinita è la fase temporale variabile.</span><span class="sxs-lookup"><span data-stu-id="4a61a-145">This StepTimer sample helper class is able to provide fixed time-step updates, as well as variable time-step updates, and the default mode is variable time steps.</span></span>

<span data-ttu-id="4a61a-146">Nel caso del rendering olografico, abbiamo scelto in modo specifico di non inserire troppa parte nella funzione timer.</span><span class="sxs-lookup"><span data-stu-id="4a61a-146">In the case of holographic rendering, we've specifically chosen not to put too much into the timer function.</span></span> <span data-ttu-id="4a61a-147">Ciò è dovuto al fatto che è possibile configurarlo in modo che sia un passaggio di tempo fisso, nel qual caso potrebbe essere chiamato più di una volta per frame, o non per alcuni frame, e gli aggiornamenti dei dati olografici dovrebbero essere eseguiti una sola volta per ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="4a61a-147">This is because you can configure it to be a fixed time step, in which case it might get called more than once per frame – or not at all, for some frames – and our holographic data updates should happen once per frame.</span></span>


<span data-ttu-id="4a61a-148">Da **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-148">From **AppMain::Update**:</span></span>

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a><span data-ttu-id="4a61a-149">Posizionare e ruotare gli ologrammi nel sistema di coordinate</span><span class="sxs-lookup"><span data-stu-id="4a61a-149">Position and rotate holograms in your coordinate system</span></span>

<span data-ttu-id="4a61a-150">Se si opera in un sistema di coordinate singolo, come nel caso del modello con il **SpatialStationaryReferenceFrame**, questo processo non è diverso da quello che viene usato altrimenti in grafica 3D.</span><span class="sxs-lookup"><span data-stu-id="4a61a-150">If you are operating in a single coordinate system, as the template does with the **SpatialStationaryReferenceFrame**, this process isn't different from what you're otherwise used to in 3D graphics.</span></span> <span data-ttu-id="4a61a-151">Qui viene ruotato il cubo e viene impostata la matrice del modello rispetto alla posizione nel sistema di coordinate fisse.</span><span class="sxs-lookup"><span data-stu-id="4a61a-151">Here, we rotate the cube and set the model matrix relative to the position in the stationary coordinate system.</span></span>

<span data-ttu-id="4a61a-152">Da **SpinningCubeRenderer:: Update**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-152">From **SpinningCubeRenderer::Update**:</span></span>

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

<span data-ttu-id="4a61a-153">**Nota sugli scenari avanzati:** Il cubo rotante è un esempio molto semplice di come posizionare un ologramma all'interno di un singolo frame di riferimento.</span><span class="sxs-lookup"><span data-stu-id="4a61a-153">**Note about advanced scenarios:** The spinning cube is a very simple example of how to position a hologram within a single reference frame.</span></span> <span data-ttu-id="4a61a-154">È anche possibile [usare più SpatialCoordinateSystems](coordinate-systems-in-directx.md) nello stesso frame sottoposto a rendering, allo stesso tempo.</span><span class="sxs-lookup"><span data-stu-id="4a61a-154">It's also possible to [use multiple SpatialCoordinateSystems](coordinate-systems-in-directx.md) in the same rendered frame, at the same time.</span></span>

### <a name="update-constant-buffer-data"></a><span data-ttu-id="4a61a-155">Aggiornare i dati del buffer costante</span><span class="sxs-lookup"><span data-stu-id="4a61a-155">Update constant buffer data</span></span>

<span data-ttu-id="4a61a-156">Le trasformazioni del modello per il contenuto vengono aggiornate come di consueto.</span><span class="sxs-lookup"><span data-stu-id="4a61a-156">Model transforms for content are updated as usual.</span></span> <span data-ttu-id="4a61a-157">A questo punto, saranno state calcolate le trasformazioni valide per il sistema di coordinate in cui verrà eseguito il rendering.</span><span class="sxs-lookup"><span data-stu-id="4a61a-157">By now, you will have computed valid transforms for the coordinate system you'll be rendering in.</span></span>

<span data-ttu-id="4a61a-158">Da **SpinningCubeRenderer:: Update**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-158">From **SpinningCubeRenderer::Update**:</span></span>

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

<span data-ttu-id="4a61a-159">Informazioni sulle trasformazioni di visualizzazione e proiezione</span><span class="sxs-lookup"><span data-stu-id="4a61a-159">What about view and projection transforms?</span></span> <span data-ttu-id="4a61a-160">Per ottenere risultati ottimali, è necessario attendere fino a quando non si è pronti per le chiamate di estrazione.</span><span class="sxs-lookup"><span data-stu-id="4a61a-160">For best results, we want to wait until we're almost ready for our draw calls before we get these.</span></span>

## <a name="render-the-current-frame"></a><span data-ttu-id="4a61a-161">Esegue il rendering del frame corrente</span><span class="sxs-lookup"><span data-stu-id="4a61a-161">Render the current frame</span></span>

<span data-ttu-id="4a61a-162">Il rendering in realtà mista di Windows non è molto diverso dal rendering in una visualizzazione mono 2D, ma è necessario tenere presente alcune differenze:</span><span class="sxs-lookup"><span data-stu-id="4a61a-162">Rendering on Windows Mixed Reality is not much different from rendering on a 2D mono display, but there are some differences you need to be aware of:</span></span>
* <span data-ttu-id="4a61a-163">Le stime del frame olografico sono importanti.</span><span class="sxs-lookup"><span data-stu-id="4a61a-163">Holographic frame predictions are important.</span></span> <span data-ttu-id="4a61a-164">Più si avvicina la stima a quando viene presentato il frame, migliore sarà l'aspetto degli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="4a61a-164">The closer the prediction is to when your frame is presented, the better your holograms will look.</span></span>
* <span data-ttu-id="4a61a-165">La realtà mista di Windows controlla le visualizzazioni della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="4a61a-165">Windows Mixed Reality controls the camera views.</span></span> <span data-ttu-id="4a61a-166">È necessario eseguire il rendering di ognuno di essi, perché il frame olografico lo mostrerà in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="4a61a-166">You need to render to each one because the holographic frame will be presenting them for you later.</span></span>
* <span data-ttu-id="4a61a-167">È consigliabile eseguire il rendering stereo usando il disegno di istanza in una matrice di destinazione di rendering.</span><span class="sxs-lookup"><span data-stu-id="4a61a-167">Stereo rendering is recommended to be accomplished using instanced drawing to a render target array.</span></span> <span data-ttu-id="4a61a-168">Il modello di app olografico usa l'approccio consigliato del disegno di istanza in una matrice di destinazione di rendering, che usa una visualizzazione della destinazione di rendering in un **Texture2DArray**.</span><span class="sxs-lookup"><span data-stu-id="4a61a-168">The holographic app template uses the recommended approach of instanced drawing to a render target array, which uses a render target view onto a **Texture2DArray**.</span></span>
* <span data-ttu-id="4a61a-169">Se si vuole eseguire il rendering senza usare le istanze stereo, è necessario creare due RenderTargetViews non di matrice (uno per ogni occhio), ognuno dei quali fa riferimento a una delle due sezioni nel **Texture2DArray** fornito all'app dal sistema.</span><span class="sxs-lookup"><span data-stu-id="4a61a-169">If you want to render without using stereo instancing, you will need to create two non-array RenderTargetViews (one for each eye) that each reference one of the two slices in the **Texture2DArray** provided to the app from the system.</span></span> <span data-ttu-id="4a61a-170">Questa operazione non è consigliata, in quanto è in genere molto più lenta rispetto all'utilizzo delle istanze.</span><span class="sxs-lookup"><span data-stu-id="4a61a-170">This is not recommended, as it is typically significantly slower than using instancing.</span></span>

### <a name="get-an-updated-holographicframe-prediction"></a><span data-ttu-id="4a61a-171">Ottenere una stima HolographicFrame aggiornata</span><span class="sxs-lookup"><span data-stu-id="4a61a-171">Get an updated HolographicFrame prediction</span></span>

<span data-ttu-id="4a61a-172">L'aggiornamento della stima dei frame migliora l'efficacia della stabilizzazione dell'immagine e consente un posizionamento più accurato degli ologrammi a causa del tempo più breve tra la stima e quando il frame è visibile all'utente.</span><span class="sxs-lookup"><span data-stu-id="4a61a-172">Updating the frame prediction enhances the effectiveness of image stabilization and allows for more accurate positioning of holograms due to the shorter time between the prediction and when the frame is visible to the user.</span></span> <span data-ttu-id="4a61a-173">Aggiornare idealmente la stima dei frame immediatamente prima del rendering.</span><span class="sxs-lookup"><span data-stu-id="4a61a-173">Ideally update your frame prediction just before rendering.</span></span>

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a><span data-ttu-id="4a61a-174">Rendering in ogni fotocamera</span><span class="sxs-lookup"><span data-stu-id="4a61a-174">Render to each camera</span></span>

<span data-ttu-id="4a61a-175">Il ciclo del set di fotocamere si pone nella stima e viene eseguito il rendering in ogni fotocamera in questo set.</span><span class="sxs-lookup"><span data-stu-id="4a61a-175">Loop on the set of camera poses in the prediction, and render to each camera in this set.</span></span>

<span data-ttu-id="4a61a-176">**Configurare la sessione di rendering**</span><span class="sxs-lookup"><span data-stu-id="4a61a-176">**Set up your rendering pass**</span></span>

<span data-ttu-id="4a61a-177">La realtà mista di Windows usa il rendering stereoscopico per migliorare l'illusione della profondità e per eseguire il rendering in modo stereoscopico, in modo che sia la visualizzazione a sinistra che quella destra siano attive</span><span class="sxs-lookup"><span data-stu-id="4a61a-177">Windows Mixed Reality uses stereoscopic rendering to enhance the illusion of depth and to render stereoscopically, so both the left and the right display are active.</span></span> <span data-ttu-id="4a61a-178">Con il rendering stereoscopico è presente un offset tra le due visualizzazioni, che il cervello può riconciliare come profondità effettiva.</span><span class="sxs-lookup"><span data-stu-id="4a61a-178">With stereoscopic rendering there is an offset between the two displays, which the brain can reconcile as actual depth.</span></span> <span data-ttu-id="4a61a-179">Questa sezione illustra il rendering stereoscopico usando le istanze, usando il codice del modello di app olografico di Windows.</span><span class="sxs-lookup"><span data-stu-id="4a61a-179">This section covers stereoscopic rendering using instancing, using code from the Windows Holographic app template.</span></span>

<span data-ttu-id="4a61a-180">Ogni fotocamera ha una propria destinazione di rendering (buffer nascosto) e matrici di visualizzazione e proiezione nello spazio olografico.</span><span class="sxs-lookup"><span data-stu-id="4a61a-180">Each camera has its own render target (back buffer), and view and projection matrices, into the holographic space.</span></span> <span data-ttu-id="4a61a-181">L'app dovrà creare altre risorse basate su fotocamera, ad esempio il buffer di profondità, per ogni singola fotocamera.</span><span class="sxs-lookup"><span data-stu-id="4a61a-181">Your app will need to create any other camera-based resources - such as the depth buffer - on a per-camera basis.</span></span> <span data-ttu-id="4a61a-182">Nel modello di app olografico di Windows, viene fornita una classe helper per raggruppare queste risorse in DX:: CameraResources.</span><span class="sxs-lookup"><span data-stu-id="4a61a-182">In the Windows Holographic app template, we provide a helper class to bundle these resources together in DX::CameraResources.</span></span> <span data-ttu-id="4a61a-183">Per iniziare, configurare le visualizzazioni della destinazione di rendering:</span><span class="sxs-lookup"><span data-stu-id="4a61a-183">Start by setting up the render target views:</span></span>

<span data-ttu-id="4a61a-184">Da **AppMain:: Render**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-184">From **AppMain::Render**:</span></span>

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

<span data-ttu-id="4a61a-185">**Utilizzare la stima per ottenere le matrici di visualizzazione e proiezione per la fotocamera**</span><span class="sxs-lookup"><span data-stu-id="4a61a-185">**Use the prediction to get the view and projection matrices for the camera**</span></span>

<span data-ttu-id="4a61a-186">Le matrici di visualizzazione e proiezione per ogni fotocamera olografica cambieranno con ogni frame.</span><span class="sxs-lookup"><span data-stu-id="4a61a-186">The view and projection matrices for each holographic camera will change with every frame.</span></span> <span data-ttu-id="4a61a-187">Aggiornare i dati nel buffer costante per ogni fotocamera olografica.</span><span class="sxs-lookup"><span data-stu-id="4a61a-187">Refresh the data in the constant buffer for each holographic camera.</span></span> <span data-ttu-id="4a61a-188">Eseguire questa operazione dopo aver aggiornato la stima e prima di effettuare qualsiasi chiamata di richiamo per la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="4a61a-188">Do this after you updated the prediction, and before you make any draw calls for that camera.</span></span>

<span data-ttu-id="4a61a-189">Da **AppMain:: Render**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-189">From **AppMain::Render**:</span></span>

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

<span data-ttu-id="4a61a-190">Qui viene illustrato come vengono acquisite le matrici dalla fotocamera.</span><span class="sxs-lookup"><span data-stu-id="4a61a-190">Here, we show how the matrices are acquired from the camera pose.</span></span> <span data-ttu-id="4a61a-191">Durante questo processo, viene anche ottenuto il viewport corrente per la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="4a61a-191">During this process we also obtain the current viewport for the camera.</span></span> <span data-ttu-id="4a61a-192">Si noti il modo in cui viene fornito un sistema di Coordinate: si tratta dello stesso sistema di coordinate usato per comprendere lo sguardo ed è uguale a quello usato per posizionare il cubo rotante.</span><span class="sxs-lookup"><span data-stu-id="4a61a-192">Note how we provide a coordinate system: this is the same coordinate system we used to understand gaze, and it's the same one we used to position the spinning cube.</span></span>


<span data-ttu-id="4a61a-193">Da **CameraResources:: UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-193">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

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

<span data-ttu-id="4a61a-194">Il viewport deve essere impostato su ogni frame.</span><span class="sxs-lookup"><span data-stu-id="4a61a-194">The viewport should be set each frame.</span></span> <span data-ttu-id="4a61a-195">Il vertex shader (almeno) deve in genere accedere ai dati di visualizzazione/proiezione.</span><span class="sxs-lookup"><span data-stu-id="4a61a-195">Your vertex shader (at least) will generally need access to the view/projection data.</span></span>


<span data-ttu-id="4a61a-196">Da **CameraResources:: AttachViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-196">From **CameraResources::AttachViewProjectionBuffer**:</span></span>

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

<span data-ttu-id="4a61a-197">**Eseguire il rendering sul buffer nascosto della fotocamera ed eseguire il commit del buffer di profondità**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-197">**Render to the camera back buffer and commit the depth buffer**:</span></span>

<span data-ttu-id="4a61a-198">È consigliabile verificare che **TryGetViewTransform** abbia avuto esito positivo prima di provare a usare i dati di visualizzazione/proiezione, perché se il sistema di coordinate non è locatable (ad esempio, il rilevamento è stato interrotto) non è possibile eseguire il rendering dell'app per quel frame.</span><span class="sxs-lookup"><span data-stu-id="4a61a-198">It's a good idea to check that **TryGetViewTransform** succeeded before trying to use the view/projection data, because if the coordinate system is not locatable (e.g., tracking was interrupted) your app cannot render with it for that frame.</span></span> <span data-ttu-id="4a61a-199">Il modello chiama solo il **rendering** sul cubo rotante se la classe **CameraResources** indica un aggiornamento riuscito.</span><span class="sxs-lookup"><span data-stu-id="4a61a-199">The template only calls **Render** on the spinning cube if the **CameraResources** class indicates a successful update.</span></span>

<span data-ttu-id="4a61a-200">Per proteggere gli ologrammi in cui uno sviluppatore o un utente li inserisce nel mondo, la realtà mista di Windows include funzionalità per la [stabilizzazione delle immagini](hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="4a61a-200">To keep holograms where a developer or a user puts them in the world, Windows Mixed Reality includes features for [image stabilization](hologram-stability.md).</span></span> <span data-ttu-id="4a61a-201">La stabilizzazione delle immagini consente di nascondere la latenza intrinseca in una pipeline di rendering per garantire la migliore esperienza olografica per gli utenti. è possibile specificare un punto di interesse per migliorare ulteriormente la stabilizzazione dell'immagine oppure è possibile fornire un buffer di profondità per calcolare la stabilizzazione delle immagini ottimizzata in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="4a61a-201">Image stabilization helps hide the latency inherent in a rendering pipeline to ensure the best holographic experiences for users; a focus point may be specified to enhance image stabilization even further, or a depth buffer may be provided to compute optimized image stabilization in real time.</span></span>

<span data-ttu-id="4a61a-202">Per ottenere risultati ottimali, l'app deve fornire un buffer di profondità usando l'API <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> .</span><span class="sxs-lookup"><span data-stu-id="4a61a-202">For best results, your app should provide a depth buffer using the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span></span> <span data-ttu-id="4a61a-203">La realtà mista di Windows può quindi usare le informazioni di geometria dal buffer di profondità per ottimizzare la stabilizzazione delle immagini in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="4a61a-203">Windows Mixed Reality can then use geometry information from the depth buffer to optimize image stabilization in real time.</span></span> <span data-ttu-id="4a61a-204">Per impostazione predefinita, il modello di app Windows olografico consente di eseguire il commit del buffer di profondità dell'app per ottimizzare la stabilità degli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="4a61a-204">The Windows Holographic app template commits the app's depth buffer by default, helping optimize hologram stability.</span></span>

<span data-ttu-id="4a61a-205">Da **AppMain:: Render**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-205">From **AppMain::Render**:</span></span>

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
><span data-ttu-id="4a61a-206">Windows elaborerà la trama di profondità sulla GPU, quindi è necessario usare il buffer di profondità come risorsa dello shader.</span><span class="sxs-lookup"><span data-stu-id="4a61a-206">Windows will process your depth texture on the GPU, so it must be possible to use your depth buffer as a shader resource.</span></span> <span data-ttu-id="4a61a-207">Il ID3D11Texture2D creato deve avere un formato senza tipo e deve essere associato come visualizzazione delle risorse dello shader.</span><span class="sxs-lookup"><span data-stu-id="4a61a-207">The ID3D11Texture2D that you create should be in a typeless format and it should be bound as a shader resource view.</span></span> <span data-ttu-id="4a61a-208">Di seguito è riportato un esempio di come creare una trama di profondità di cui è possibile eseguire il commit per la stabilizzazione delle immagini.</span><span class="sxs-lookup"><span data-stu-id="4a61a-208">Here is an example of how to create a depth texture that can be committed for image stabilization.</span></span>

<span data-ttu-id="4a61a-209">Codice per la **creazione di risorse del buffer di profondità per CommitDirect3D11DepthBuffer**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-209">Code for **Depth buffer resource creation for CommitDirect3D11DepthBuffer**:</span></span>

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

<span data-ttu-id="4a61a-210">**Creare contenuto olografico**</span><span class="sxs-lookup"><span data-stu-id="4a61a-210">**Draw holographic content**</span></span>

<span data-ttu-id="4a61a-211">Il modello di app olografico di Windows esegue il rendering del contenuto in stereo usando la tecnica consigliata per il disegno di una geometria di istanza in un Texture2DArray di dimensioni 2.</span><span class="sxs-lookup"><span data-stu-id="4a61a-211">The Windows Holographic app template renders content in stereo by using the recommended technique of drawing instanced geometry to a Texture2DArray of size 2.</span></span> <span data-ttu-id="4a61a-212">Esaminiamo la parte relativa alle istanze e il funzionamento della realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="4a61a-212">Let's look at the instancing part of this, and how it works on Windows Mixed Reality.</span></span>

<span data-ttu-id="4a61a-213">Da **SpinningCubeRenderer:: Render**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-213">From **SpinningCubeRenderer::Render**:</span></span>

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

<span data-ttu-id="4a61a-214">Ogni istanza accede a una matrice di visualizzazione/proiezione diversa dal buffer costante.</span><span class="sxs-lookup"><span data-stu-id="4a61a-214">Each instance accesses a different view/projection matrix from the constant buffer.</span></span> <span data-ttu-id="4a61a-215">Di seguito è illustrata la struttura del buffer costante, che è solo una matrice di 2 matrici.</span><span class="sxs-lookup"><span data-stu-id="4a61a-215">Here's the constant buffer structure, which is just an array of 2 matrices.</span></span>

<span data-ttu-id="4a61a-216">Da **VertexShaderShared. HLSL**, incluso in **VPRTVertexShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-216">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

<span data-ttu-id="4a61a-217">Per ogni pixel è necessario impostare l'indice della matrice di destinazione di rendering.</span><span class="sxs-lookup"><span data-stu-id="4a61a-217">The render target array index must be set for each pixel.</span></span> <span data-ttu-id="4a61a-218">Nel frammento di codice seguente viene eseguito il mapping di output. viewId alla semantica **SV_RenderTargetArrayIndex** .</span><span class="sxs-lookup"><span data-stu-id="4a61a-218">In the following snippet, output.viewId is mapped to the **SV_RenderTargetArrayIndex** semantic.</span></span> <span data-ttu-id="4a61a-219">Si noti che è necessario il supporto per una funzionalità facoltativa Direct3D 11,3, che consente di impostare la semantica dell'indice della matrice di destinazione di rendering da qualsiasi fase dello shader.</span><span class="sxs-lookup"><span data-stu-id="4a61a-219">Note that this requires support for an optional Direct3D 11.3 feature, which allows the render target array index semantic to be set from any shader stage.</span></span>

<span data-ttu-id="4a61a-220">Da **VPRTVertexShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-220">From **VPRTVertexShader.hlsl**:</span></span>

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

<span data-ttu-id="4a61a-221">Da **VertexShaderShared. HLSL**, incluso in **VPRTVertexShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-221">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

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

<span data-ttu-id="4a61a-222">Se si desidera utilizzare le tecniche di disegno con istanze esistenti con questo metodo di disegno in una matrice di destinazione di rendering stereo, è sufficiente disegnare il numero di istanze di cui si dispone normalmente.</span><span class="sxs-lookup"><span data-stu-id="4a61a-222">If you want to use your existing instanced drawing techniques with this method of drawing to a stereo render target array, all you have to do is draw twice the number of instances you normally have.</span></span> <span data-ttu-id="4a61a-223">Nello shader dividere **input. IDIstanza** per 2 per ottenere l'ID istanza originale, che può essere indicizzato in (ad esempio) un buffer di dati per oggetto: `int actualIdx = input.instId / 2;`</span><span class="sxs-lookup"><span data-stu-id="4a61a-223">In the shader, divide **input.instId** by 2 to get the original instance ID, which can be indexed into (for example) a buffer of per-object data: `int actualIdx = input.instId / 2;`</span></span>

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a><span data-ttu-id="4a61a-224">Nota importante sul rendering del contenuto stereo in HoloLens</span><span class="sxs-lookup"><span data-stu-id="4a61a-224">Important note about rendering stereo content on HoloLens</span></span>

<span data-ttu-id="4a61a-225">La realtà mista di Windows supporta la possibilità di impostare l'indice della matrice di destinazione di rendering da qualsiasi fase dello shader. in genere, si tratta di un'attività che può essere eseguita solo nella fase geometry shader a causa del modo in cui la semantica è definita per Direct3D 11.</span><span class="sxs-lookup"><span data-stu-id="4a61a-225">Windows Mixed Reality supports the ability to set the render target array index from any shader stage; normally, this is a task that could only be done in the geometry shader stage due to the way the semantic is defined for Direct3D 11.</span></span> <span data-ttu-id="4a61a-226">Qui viene illustrato un esempio completo di come configurare una pipeline di rendering solo con le fasi Vertex e pixel shader impostate.</span><span class="sxs-lookup"><span data-stu-id="4a61a-226">Here, we show a complete example of how to set up a rendering pipeline with just the vertex and pixel shader stages set.</span></span> <span data-ttu-id="4a61a-227">Il codice dello shader è come descritto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="4a61a-227">The shader code is as described above.</span></span>

<span data-ttu-id="4a61a-228">Da **SpinningCubeRenderer:: Render**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-228">From **SpinningCubeRenderer::Render**:</span></span>

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a><span data-ttu-id="4a61a-229">Nota importante sul rendering nei dispositivi non HoloLens</span><span class="sxs-lookup"><span data-stu-id="4a61a-229">Important note about rendering on non-HoloLens devices</span></span>

<span data-ttu-id="4a61a-230">Per impostare l'indice della matrice di destinazione di rendering nel vertex shader, è necessario che il driver di grafica supporti una funzionalità facoltativa Direct3D 11,3, supportata da HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4a61a-230">Setting the render target array index in the vertex shader requires that the graphics driver supports an optional Direct3D 11.3 feature, which HoloLens does support.</span></span> <span data-ttu-id="4a61a-231">L'app potrebbe essere in grado di implementare in modo sicuro solo questa tecnica per il rendering e tutti i requisiti verranno soddisfatti per l'esecuzione in Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4a61a-231">Your app may be able to safely implement just that technique for rendering, and all requirements will be met for running on the Microsoft HoloLens.</span></span>

<span data-ttu-id="4a61a-232">È possibile che si voglia usare anche l'emulatore di HoloLens, che può essere uno strumento di sviluppo potente per l'app olografica e per supportare i dispositivi con auricolari a realtà mista di Windows, collegati a PC Windows 10.</span><span class="sxs-lookup"><span data-stu-id="4a61a-232">It may be the case that you want to use the HoloLens emulator as well, which can be a powerful development tool for your holographic app - and support Windows Mixed Reality immersive headset devices that are attached to Windows 10 PCs.</span></span> <span data-ttu-id="4a61a-233">Supporto per il percorso di rendering non HoloLens e pertanto, per tutte le realtà miste di Windows, è anche incorporato nel modello di app olografico di Windows.</span><span class="sxs-lookup"><span data-stu-id="4a61a-233">Support for the non-HoloLens rendering path - and therefore, for all of Windows Mixed Reality - is also built into the Windows Holographic app template.</span></span> <span data-ttu-id="4a61a-234">Nel codice del modello, è possibile trovare il codice per abilitare l'esecuzione dell'app olografica sulla GPU nel PC di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="4a61a-234">In the template code, you will find code to enable your holographic app to run on the GPU in your development PC.</span></span> <span data-ttu-id="4a61a-235">Ecco come la classe **DeviceResources** verifica la presenza di questo supporto della funzionalità facoltativa.</span><span class="sxs-lookup"><span data-stu-id="4a61a-235">Here is how the **DeviceResources** class checks for this optional feature support.</span></span>

<span data-ttu-id="4a61a-236">Da **DeviceResources:: CreateDeviceResources**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-236">From **DeviceResources::CreateDeviceResources**:</span></span>

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

<span data-ttu-id="4a61a-237">Per supportare il rendering senza questa funzionalità facoltativa, l'app deve usare un geometry shader per impostare l'indice della matrice di destinazione di rendering.</span><span class="sxs-lookup"><span data-stu-id="4a61a-237">To support rendering without this optional feature, your app must use a geometry shader to set the render target array index.</span></span> <span data-ttu-id="4a61a-238">Questo frammento di codice verrà aggiunto *dopo* **VSSetConstantBuffers**e *prima* di **PSSetShader** nell'esempio di codice illustrato nella sezione precedente, in cui viene illustrato come eseguire il rendering dello stereo su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4a61a-238">This snippet would be added *after* **VSSetConstantBuffers**, and *before* **PSSetShader** in the code example shown in the previous section that explains how to render stereo on HoloLens.</span></span>

<span data-ttu-id="4a61a-239">Da **SpinningCubeRenderer:: Render**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-239">From **SpinningCubeRenderer::Render**:</span></span>

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

<span data-ttu-id="4a61a-240">**HLSL nota**: in questo caso, è necessario caricare anche un vertex shader leggermente modificato che passa l'indice della matrice di destinazione di rendering a geometry shader usando una semantica shader sempre consentita, ad esempio TEXCOORD0.</span><span class="sxs-lookup"><span data-stu-id="4a61a-240">**HLSL NOTE**: In this case, you must also load a slightly modified vertex shader that passes the render target array index to the geometry shader using an always-allowed shader semantic, such as TEXCOORD0.</span></span> <span data-ttu-id="4a61a-241">Il geometry shader non deve eseguire alcuna operazione; il modello geometry shader passa attraverso tutti i dati, fatta eccezione per l'indice della matrice di destinazione di rendering, che viene usato per impostare la semantica del SV_RenderTargetArrayIndex.</span><span class="sxs-lookup"><span data-stu-id="4a61a-241">The geometry shader does not have to do any work; the template geometry shader passes through all data, with the exception of the render target array index, which is used to set the SV_RenderTargetArrayIndex semantic.</span></span>

<span data-ttu-id="4a61a-242">Codice modello app per **GeometryShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-242">App template code for **GeometryShader.hlsl**:</span></span>

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

## <a name="present"></a><span data-ttu-id="4a61a-243">Presenti</span><span class="sxs-lookup"><span data-stu-id="4a61a-243">Present</span></span>

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a><span data-ttu-id="4a61a-244">Abilitare il frame olografico per presentare la catena di scambio</span><span class="sxs-lookup"><span data-stu-id="4a61a-244">Enable the holographic frame to present the swap chain</span></span>

<span data-ttu-id="4a61a-245">Con la realtà mista di Windows, il sistema controlla la catena di scambio.</span><span class="sxs-lookup"><span data-stu-id="4a61a-245">With Windows Mixed Reality, the system controls the swap chain.</span></span> <span data-ttu-id="4a61a-246">Il sistema gestisce quindi la presentazione dei frame a ogni fotocamera olografica per garantire un'esperienza utente di alta qualità.</span><span class="sxs-lookup"><span data-stu-id="4a61a-246">The system then manages presenting frames to each holographic camera to ensure a high quality user experience.</span></span> <span data-ttu-id="4a61a-247">Fornisce anche un viewport per aggiornare ogni frame, per ogni fotocamera, per ottimizzare gli aspetti del sistema, ad esempio la stabilizzazione dell'immagine o l'acquisizione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="4a61a-247">It also provides a viewport update each frame, for each camera, to optimize aspects of the system such as image stabilization or Mixed Reality Capture.</span></span> <span data-ttu-id="4a61a-248">Quindi, un'app olografica che usa DirectX non chiama **presente** in una catena di scambio dxgi.</span><span class="sxs-lookup"><span data-stu-id="4a61a-248">So, a holographic app using DirectX doesn't call **Present** on a DXGI swap chain.</span></span> <span data-ttu-id="4a61a-249">Al contrario, si usa la classe <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> per presentare tutti i le catene per un frame al termine del disegno.</span><span class="sxs-lookup"><span data-stu-id="4a61a-249">Instead, you use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class to present all swapchains for a frame once you're done drawing it.</span></span>

<span data-ttu-id="4a61a-250">Da **DeviceResources::P inviato nuovamente**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-250">From **DeviceResources::Present**:</span></span>

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

<span data-ttu-id="4a61a-251">Per impostazione predefinita, questa API attende il completamento del frame prima della restituzione.</span><span class="sxs-lookup"><span data-stu-id="4a61a-251">By default, this API waits for the frame to finish before it returns.</span></span> <span data-ttu-id="4a61a-252">Le app olografiche devono attendere il completamento del frame precedente prima di iniziare a lavorare su un nuovo frame, perché questo riduce la latenza e consente di ottenere risultati migliori dalle stime dei frame olografici.</span><span class="sxs-lookup"><span data-stu-id="4a61a-252">Holographic apps should wait for the previous frame to finish before starting work on a new frame, because this reduces latency and allows for better results from holographic frame predictions.</span></span> <span data-ttu-id="4a61a-253">Questa regola non è rigida e se sono presenti frame che impostano più di un aggiornamento dello schermo per il rendering, è possibile disabilitare questa attesa passando il parametro HolographicFramePresentWaitBehavior a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span><span class="sxs-lookup"><span data-stu-id="4a61a-253">This isn't a hard rule, and if you have frames that take longer than one screen refresh to render you can disable this wait by passing the HolographicFramePresentWaitBehavior parameter to <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span></span> <span data-ttu-id="4a61a-254">In questo caso, è probabile che si utilizzi un thread di rendering asincrono per mantenere un carico continuo sulla GPU.</span><span class="sxs-lookup"><span data-stu-id="4a61a-254">In this case, you would likely use an asynchronous rendering thread in order to maintain a continuous load on the GPU.</span></span> <span data-ttu-id="4a61a-255">Si noti che la frequenza di aggiornamento del dispositivo HoloLens è 60Hz, dove un frame ha una durata di circa 16 ms.</span><span class="sxs-lookup"><span data-stu-id="4a61a-255">Note that the refresh rate of the HoloLens device is 60hz, where one frame has a duration of approximately 16 ms.</span></span> <span data-ttu-id="4a61a-256">I dispositivi per auricolari immersivi possono variare da 60Hz a 90Hz; Quando si aggiorna la visualizzazione a 90 Hz, ogni frame avrà una durata pari a circa 11 ms.</span><span class="sxs-lookup"><span data-stu-id="4a61a-256">Immersive headset devices can range from 60hz to 90hz; when refreshing the display at 90 hz, each frame will have a duration of approximately 11 ms.</span></span>

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a><span data-ttu-id="4a61a-257">Gestire scenari DeviceLost in collaborazione con HolographicFrame</span><span class="sxs-lookup"><span data-stu-id="4a61a-257">Handle DeviceLost scenarios in cooperation with the HolographicFrame</span></span>

<span data-ttu-id="4a61a-258">Le app DirectX 11 in genere vogliono controllare il valore HRESULT restituito dalla funzione **presente** della catena di scambio DXGI per determinare se si è verificato un errore **DeviceLost** .</span><span class="sxs-lookup"><span data-stu-id="4a61a-258">DirectX 11 apps would typically want to check the HRESULT returned by the DXGI swap chain's **Present** function to find out if there was a **DeviceLost** error.</span></span> <span data-ttu-id="4a61a-259">La classe <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> gestisce questa operazione automaticamente.</span><span class="sxs-lookup"><span data-stu-id="4a61a-259">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class handles this for you.</span></span> <span data-ttu-id="4a61a-260">Esaminare il <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> che restituisce per scoprire se è necessario rilasciare e ricreare il dispositivo Direct3D e le risorse basate su dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4a61a-260">Inspect the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> it returns to find out if you need to release and recreate the Direct3D device and device-based resources.</span></span>

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

<span data-ttu-id="4a61a-261">Si noti che se il dispositivo Direct3D è stato perso ed è stato ricreato, è necessario indicare all' <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> di iniziare a usare il nuovo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4a61a-261">Note that if the Direct3D device was lost, and you did recreate it, you have to tell the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> to start using the new device.</span></span> <span data-ttu-id="4a61a-262">La catena di scambio verrà ricreata per questo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4a61a-262">The swap chain will be recreated for this device.</span></span>

<span data-ttu-id="4a61a-263">Da **DeviceResources:: InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-263">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

<span data-ttu-id="4a61a-264">Una volta visualizzato il frame, è possibile tornare al ciclo principale del programma e consentirne la continuazione al frame successivo.</span><span class="sxs-lookup"><span data-stu-id="4a61a-264">Once your frame is presented, you can return back to the main program loop and allow it to continue to the next frame.</span></span>

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a><span data-ttu-id="4a61a-265">Computer grafici ibridi e applicazioni di realtà mista</span><span class="sxs-lookup"><span data-stu-id="4a61a-265">Hybrid graphics PCs and mixed reality applications</span></span>

<span data-ttu-id="4a61a-266">I PC Windows 10 Creators Update possono essere configurati con GPU **sia** discrete che integrate.</span><span class="sxs-lookup"><span data-stu-id="4a61a-266">Windows 10 Creators Update PCs may be configured with **both** discrete and integrated GPUs.</span></span> <span data-ttu-id="4a61a-267">Con questi tipi di computer, Windows sceglierà la scheda a cui è connessa l'auricolare.</span><span class="sxs-lookup"><span data-stu-id="4a61a-267">With these types of computers, Windows will choose the adapter the headset is connected to.</span></span> <span data-ttu-id="4a61a-268">Le applicazioni devono garantire che il dispositivo DirectX creato usi la stessa scheda.</span><span class="sxs-lookup"><span data-stu-id="4a61a-268">Applications must ensure the DirectX device it creates uses the same adapter.</span></span>

<span data-ttu-id="4a61a-269">La maggior parte del codice di esempio Direct3D generale illustra la creazione di un dispositivo DirectX usando la scheda hardware predefinita, che in un sistema ibrido potrebbe non essere uguale a quella usata per l'auricolare.</span><span class="sxs-lookup"><span data-stu-id="4a61a-269">Most general Direct3D sample code demonstrates creating a DirectX device using the default hardware adapter, which on a hybrid system may not be the same as the one used for the headset.</span></span>

<span data-ttu-id="4a61a-270">Per ovviare a eventuali problemi che possono verificarsi, utilizzare <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> da <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>. PrimaryAdapterId () o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>. AdapterId ().</span><span class="sxs-lookup"><span data-stu-id="4a61a-270">To work around any issues this may cause, use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> from either <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>.PrimaryAdapterId() or <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>.AdapterId().</span></span> <span data-ttu-id="4a61a-271">Questo adapterId può quindi essere usato per selezionare il DXGIAdapter corretto usando IDXGIFactory4. EnumAdapterByLuid.</span><span class="sxs-lookup"><span data-stu-id="4a61a-271">This adapterId can then be used to select the right DXGIAdapter using IDXGIFactory4.EnumAdapterByLuid.</span></span>

<span data-ttu-id="4a61a-272">Da **DeviceResources:: InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-272">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

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

<span data-ttu-id="4a61a-273">Codice per l' **aggiornamento di DeviceResources:: CreateDeviceResources per l'uso di IDXGIAdapter**</span><span class="sxs-lookup"><span data-stu-id="4a61a-273">Code to **update DeviceResources::CreateDeviceResources to use IDXGIAdapter**</span></span>

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

<span data-ttu-id="4a61a-274">**Grafica ibrida e Media Foundation**</span><span class="sxs-lookup"><span data-stu-id="4a61a-274">**Hybrid graphics and Media Foundation**</span></span>

<span data-ttu-id="4a61a-275">L'uso di Media Foundation nei sistemi ibridi può causare problemi se il rendering dei video non è danneggiato o la trama video è danneggiata.</span><span class="sxs-lookup"><span data-stu-id="4a61a-275">Using Media Foundation on hybrid systems may cause issues where video will not render or video texture is corrupt.</span></span> <span data-ttu-id="4a61a-276">Questa situazione può verificarsi perché Media Foundation viene impostato come valore predefinito su un comportamento del sistema come indicato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="4a61a-276">This can occur because Media Foundation is defaulting to a system behavior as mentioned above.</span></span> <span data-ttu-id="4a61a-277">In alcuni scenari, la creazione di un ID3D11Device separato è necessaria per supportare il multithreading e vengono impostati i flag di creazione corretti.</span><span class="sxs-lookup"><span data-stu-id="4a61a-277">In some scenarios, creating a separate ID3D11Device is required to support multi-threading and the correct creation flags are set.</span></span>

<span data-ttu-id="4a61a-278">Durante l'inizializzazione di ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag deve essere definito come parte del D3D11_CREATE_DEVICE_FLAG.</span><span class="sxs-lookup"><span data-stu-id="4a61a-278">When initializing the ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag must be defined as part of the D3D11_CREATE_DEVICE_FLAG.</span></span> <span data-ttu-id="4a61a-279">Una volta creato il dispositivo e il contesto, chiamare <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> per abilitare il multithreading.</span><span class="sxs-lookup"><span data-stu-id="4a61a-279">Once the device and context is created, call <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> to enable multithreading.</span></span> <span data-ttu-id="4a61a-280">Per associare il dispositivo a <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, usare la funzione <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager:: ResetDevice</a> .</span><span class="sxs-lookup"><span data-stu-id="4a61a-280">To associate the device with the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> function.</span></span>

<span data-ttu-id="4a61a-281">Codice per **associare un ID3D11Device a IMFDXGIDeviceManager**:</span><span class="sxs-lookup"><span data-stu-id="4a61a-281">Code to **associate a ID3D11Device with IMFDXGIDeviceManager**:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4a61a-282">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4a61a-282">See also</span></span>
* [<span data-ttu-id="4a61a-283">Sistemi di coordinate in DirectX</span><span class="sxs-lookup"><span data-stu-id="4a61a-283">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="4a61a-284">Uso dell'emulatore HoloLens</span><span class="sxs-lookup"><span data-stu-id="4a61a-284">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)

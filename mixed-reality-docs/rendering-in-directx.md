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
# <a name="rendering-in-directx"></a>Per il rendering in DirectX

Realtà mista di Windows si basa su DirectX per produrre avanzata, grafica 3D esperienze per gli utenti. L'astrazione per il rendering si trova immediatamente sopra DirectX e di un motivo app sulla posizione e l'orientamento di uno o più Observer di una scena holographic, come previsto dal sistema. Lo sviluppatore può individuare i vntana relativo ogni videocamera, consentendo all'app di rendering questi vntana in vari sistemi di coordinate spaziali, come l'utente si sposta.

## <a name="update-for-the-current-frame"></a>Aggiornamento per il frame corrente

Per aggiornare lo stato dell'applicazione per vntana, una volta per ogni fotogramma dell'app sarà:
* Ottenere un <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> dal sistema di gestione di visualizzazione.
* Eseguire il rendering della scena con la stima corrente in cui la visualizzazione della fotocamera sarà quando è stato completato. Si noti che possono essere presenti più di una fotocamera per la scena holographic.

Per eseguire il rendering per le visualizzazioni di fotocamera holographic, una volta per ogni fotogramma dell'app sarà:
* Per ogni videocamera, eseguire il rendering della scena per il frame corrente, usando le matrici di visualizzazione e di proiezione della fotocamera dal sistema.

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a>Creare un nuovo frame holographic e ottenere la stima

Il <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> dispone di informazioni che l'app necessita per aggiornare ed eseguire il rendering il frame corrente. L'app viene avviata ogni nuovo frame chiamando il **CreateNextFrame** (metodo). Quando questo metodo viene chiamato, le previsioni vengono eseguite usando i dati di sensori più recenti disponibili e incapsulati nella **CurrentPrediction** oggetto.

Un nuovo oggetto frame da utilizzare per ogni fotogramma sottoposto a rendering come è valido solo per un istante nel tempo. Il **CurrentPrediction** proprietà contiene informazioni quali la posizione della camera. Le informazioni sono estrapolate per il momento esatto in cui è previsto che il frame sia visibile all'utente.

Il codice seguente è un estratto **AppMain::Update**:

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a>Elaborazione degli aggiornamenti della fotocamera

I buffer nascosti modificabili da fotogramma per fotogramma. Le esigenze delle app per convalidare la parte posteriore del buffer per ogni videocamera e rilasciano e ricreare le viste di risorsa e i buffer di profondità in base alle esigenze. Si noti che il set di può causare nella stima è l'elenco autorevole delle videocamere utilizzato nel frame corrente. È in genere, usare questo elenco per eseguire l'iterazione sul set di fotocamere digitali.

Dal **AppMain::Update**:

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

Dal **DeviceResources::EnsureCameraResources**:

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a>Ottenere il sistema di coordinate da utilizzare come base per il rendering

Realtà mista di Windows consente all'app di creare vari [sistemi di coordinate](coordinate-systems-in-directx.md) in base alle esigenze, ad esempio il frame di riferimento collegati e il frame di riferimento fisso, che tengono traccia dei percorsi nel mondo fisico. L'app può quindi usare questi sistemi di coordinate per motivo sulla posizione in cui eseguire il rendering di ogni fotogramma vntana. Quando si richiedono le coordinate da un'API, verrà sempre passato il <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> all'interno di cui si desidera queste coordinate per esprimere.

Dal **AppMain::Update**:

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

Questi sistemi di coordinate è quindi utilizzabile per generare matrici stereo visualizzazione durante il rendering del contenuto nella scena.

From **CameraResources::UpdateViewProjectionBuffer**:

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a>Sguardo processo e il movimento di input

[Estasiati](gaze-in-directx.md) e [mano](hands-and-motion-controllers-in-directx.md) non sono basati sul tempo di input e pertanto non è necessario aggiornare il **StepTimer** (funzione). Tuttavia questo input è qualcosa che l'app deve esaminare ogni fotogramma.

### <a name="process-time-based-updates"></a>Elaborazione degli aggiornamenti basati sul tempo

Qualsiasi app in tempo reale per il rendering sarà necessario trovare un modo per elaborare gli aggiornamenti basati sul tempo. Offriamo un modo per eseguire questa operazione nel modello di app Windows Holographic tramite un **StepTimer** implementazione. Ciò è simile al StepTimer fornito nel modello di app DirectX 11 UWP, pertanto se sono già stati analizzati tale modello dovrebbe essere familiare attraverso modalità. Questa classe helper di esempio StepTimer è in grado di fornire aggiornamenti intervallo temporale fissi, nonché gli aggiornamenti di variabile-intervallo temporale e la modalità predefinita è intervalli temporali di variabile.

Nel caso di rendering holographic, abbiamo scelto in modo specifico per non inserire troppi alla funzione timer. Infatti, è possibile configurare in modo che sia un passaggio di tempo fisso, nel qual caso potrebbe essere chiamata più volte per ogni fotogramma, o non ereditarli affatto, per alcuni fotogrammi – e gli aggiornamenti dati holographic devono avvengono una sola volta per ogni fotogramma.


Dal **AppMain::Update**:

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a>Posizione e la rotazione vntana nel sistema di coordinate

Se si opera in un singolo sistema di coordinate, così come il modello con il **SpatialStationaryReferenceFrame**, questo processo non è diverso da quello che si sta in caso contrario utilizzate per nella grafica 3D. In questo caso, si ruota il cubo e imposta la matrice di modello rispetto alla posizione nel sistema di coordinate fermo.

From **SpinningCubeRenderer::Update**:

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

**Nota sugli scenari avanzati:** Il cubo rotante è un esempio molto semplice di come posizionare un ologrammi all'interno di un singolo fotogramma di riferimento. È anche possibile [utilizzare più SpatialCoordinateSystems](coordinate-systems-in-directx.md) nello stesso frame sottoposto a rendering, nello stesso momento.

### <a name="update-constant-buffer-data"></a>Aggiornare i dati nel buffer costanti

Trasformazioni di modello per il contenuto vengono aggiornate come di consueto. A questo punto, si verranno calcolata trasformazioni valide per il sistema di coordinate in che è sarà per il rendering.

From **SpinningCubeRenderer::Update**:

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

Per quanto riguarda le trasformazioni di proiezione e di visualizzazione? Per ottenere risultati ottimali, si vuole attendere fino a quando non si è quasi pronti per le chiamate di disegno prima di addentrarsi questi.

## <a name="render-the-current-frame"></a>Eseguire il rendering il frame corrente

Il rendering in realtà mista di Windows non è molto diverso dal rendering su uno schermo di mono 2D, ma esistono alcune differenze di che è necessario essere a conoscenza:
* Le stime holographic frame sono importanti. Si avvicina alla stima consiste nella quando viene presentato il frame, migliore sarà il vntana avrà un aspetto.
* Realtà mista di Windows controlla le viste della fotocamera. È necessario eseguire il rendering in ciascuno di essi in quanto il frame holographic terrà una presentazione li automaticamente in un secondo momento.
* È consigliabile stereo per il rendering di questo strumento equivalgano disegno creato in una matrice di destinazione di rendering. Il modello di app holographic Usa l'approccio consigliato di disegno creato in una matrice di destinazione di rendering, che usa una visualizzazione destinazione rendering su un **Texture2DArray**.
* Se si desidera eseguire il rendering senza l'utilizzo delle istanze stereo, è necessario creare due RenderTargetViews non di matrice, una per ogni sotto controllo, che ogni riferimento uno dei due periodi nel **Texture2DArray** fornita per l'app dal sistema. Ciò non è consigliabile, perché è in genere notevolmente più lento rispetto all'uso delle istanze.

### <a name="get-an-updated-holographicframe-prediction"></a>Ottenere una stima HolographicFrame aggiornato

L'aggiornamento alla stima di frame migliora l'efficacia di stabilizzazione di immagine e consente il posizionamento più preciso di vntana a causa del tempo più breve tra la stima e quando il frame è visibile all'utente. In teoria, aggiornare la stima di frame appena prima del rendering.

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a>Eseguire il rendering per ogni videocamera

Il ciclo sul set di fotocamera può causare la stima e il rendering a ogni tipo di camera in questo set.

**Configurare il passaggio di rendering**

Realtà mista di Windows usa per il rendering stereoscopico per migliorare l'illusione di profondità e per eseguire il rendering stereoscopicamente, in modo da sinistra e la visualizzazione a destra sono attivi. Con il rendering stereoscopico è presente un offset da una schermata, che può risolvere le differenze tra il cervello come profondità effettivo. Questa sezione illustra stereoscopico per il rendering tramite la creazione di istanze, tramite codice dal modello di app Windows Holographic.

Ogni videocamera ha il proprio rendering (buffer nascosto), destinazione e di visualizzazione e di proiezione le matrici, nello spazio holographic. L'app dovrà creare qualsiasi altra basata su fotocamera risorsa - ad esempio il buffer di profondità - pagamento in base al fotocamera. Il modello di app Windows Holographic, fornisce una classe helper per creare un bundle queste risorse insieme in DX::CameraResources. Inizia configurando le visualizzazioni destinazione rendering:

Dal **AppMain::Render**:

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

**Usare la stima per ottenere le matrici di visualizzazione e di proiezione della fotocamera**

Le matrici di visualizzazione e di proiezione per ogni videocamera holographic verranno modificato con ogni fotogramma. Aggiornare i dati nel buffer di costanti per ogni videocamera holographic. Eseguire questa operazione dopo che è stato aggiornato di stima, e prima di apportare qualsiasi draw chiama per tale fotocamera.

Dal **AppMain::Render**:

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

Di seguito viene illustrato come le matrici vengono acquisite dal posa fotocamera. Durante questo processo è anche possibile ottenere il viewport per la fotocamera. Si noti come presentiamo un sistema di coordinate: questo è il sistema di coordinate stesso è stato usato per comprendere sguardo ed è uguale a quello abbiamo usati per posizionare il cubo rotante.


From **CameraResources::UpdateViewProjectionBuffer**:

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

Il viewport deve essere impostato ogni fotogramma. Shader vertice (minimo) in genere necessario accedere ai dati di visualizzazione o di proiezione.


Dal **CameraResources::AttachViewProjectionBuffer**:

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

**Eseguire il rendering per il buffer nascosto della fotocamera ed eseguire il commit il buffer di profondità**:

È una buona idea per verificare che **TryGetViewTransform** ha avuto esito positivo prima di provare a usare i dati di visualizzazione o di proiezione, in quanto se il sistema di coordinate non è individuabile (ad esempio, il rilevamento è stata interrotta) l'app non è possibile eseguire il rendering con esso per tale frame. Il modello chiama solo **eseguire il rendering** sul cubo rotante se il **CameraResources** classe indica che l'aggiornamento.

Per mantenere vntana in cui uno sviluppatore o un utente li inserisce nel mondo, realtà mista di Windows include funzionalità per [immagine della stabilizzazione](hologram-stability.md). Stabilizzazione immagine consente di nascondere la latenza intrinseca in una pipeline di rendering per garantire le migliori esperienze holographic per gli utenti; un punto di stato attivo può essere specificato per migliorare ulteriormente la stabilizzazione immagine o un buffer di profondità può essere fornito per il calcolo con ottimizzazione per la stabilizzazione immagine in tempo reale.

Per ottenere risultati ottimali, l'app deve fornire un buffer di profondità tramite il <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API. Realtà mista di Windows possono utilizzare informazioni geometry dal buffer di profondità per ottimizzare la stabilizzazione immagine in tempo reale. Il modello di app per Windows Holographic esegue il commit del buffer di profondità dell'app per impostazione predefinita, consentire l'ottimizzazione della stabilità di ologramma.

Dal **AppMain::Render**:

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
>Windows elabora la trama profondità nella GPU, pertanto deve essere possibile usare i buffer di profondità come una risorsa shader. ID3D11Texture2D creato deve essere in un formato senza tipo e deve essere associato come una visualizzazione di risorse shader. Di seguito è riportato un esempio di come creare una trama di profondità che può essere eseguito il commit per la stabilizzazione immagine.

Codice per un **creazione di risorse di buffer di profondità per CommitDirect3D11DepthBuffer**:

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

**Creazione del contenuto holographic**

Il modello di app per Windows Holographic esegue il rendering di contenuto nel formato stereo usando la tecnica consigliata di disegno di istanza geometry da un Texture2DArray di dimensione 2. Esaminiamo la parte delle istanze di questo e il funzionamento in realtà mista di Windows.

From **SpinningCubeRenderer::Render**:

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

Ogni istanza accede a una matrice di proiezione/vista diverso dal buffer costante. Ecco la struttura di buffer costante, che è semplicemente una matrice di 2 matrici.

Dal **VertexShaderShared.hlsl**, incluso dal **VPRTVertexShader.hlsl**:

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

Indice della matrice di destinazione rendering deve essere impostata per ogni pixel. Nel frammento di codice seguente, output.viewId viene eseguito il mapping per il **SV_RenderTargetArrayIndex** semantico. Si noti che questa operazione richiede il supporto per una funzionalità di Direct3D 11.3 facoltativa, che consente l'indice di matrice di destinazione rendering semantica impostarla da qualsiasi fase dello shader.

Dal **VPRTVertexShader.hlsl**:

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

Dal **VertexShaderShared.hlsl**, incluso dal **VPRTVertexShader.hlsl**:

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

Se si desidera utilizzare le proprie creata un'istanza di matrice di destinazione eseguire il rendering di tecniche di disegnare con questo metodo di disegno di un impianto stereo, tutto è necessario eseguire è creare due volte il numero di istanze in genere necessario. Nello shader, dividere **input.instId** da 2 a ottenere l'ID istanza originale, che possono essere indicizzati, ad esempio, un buffer di dati per ogni oggetto: `int actualIdx = input.instId / 2;`

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a>Nota importante sul rendering del contenuto stereo su HoloLens

Realtà mista di Windows supporta la possibilità di impostare l'indice di matrice di destinazione rendering da qualsiasi fase dello shader; in genere, si tratta di un'attività che poteva essere eseguita solo nella fase geometry shader a causa del modo in cui che la semantica viene definita per Direct3D 11. Di seguito viene illustrato un esempio completo di come configurare una pipeline di rendering con solo il pixel e vertex shader fasi set. Il codice dello shader è come descritto in precedenza.

From **SpinningCubeRenderer::Render**:

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a>Nota importante sul rendering sui dispositivi non HoloLens

L'impostazione di indice di matrice di destinazione di rendering nel vertex shader richiede che il driver di grafica supporta una funzionalità di Direct3D 11.3 facoltativa, che supporta HoloLens. L'app potrebbe essere in grado di implementare in modo sicuro solo tale tecnica per il rendering e tutti i requisiti per l'esecuzione in di Microsoft HoloLens.

Potrebbe essere il caso che si desidera utilizzare HoloLens emulatore, che può essere uno strumento di sviluppo avanzato per l'app holographic - e supportare i dispositivi visore VR immersivi realtà mista di Windows che sono collegati a PC Windows 10. Supporto per il percorso per il rendering non HoloLens - e di conseguenza, per tutti di realtà mista di Windows - viene compilato nel modello di app Windows Holographic. Nel codice del modello, si noterà codice per abilitare l'app holographic per l'esecuzione sulla GPU nel PC di sviluppo. Ecco come la **DeviceResources** classe controlli per il supporto di questa funzionalità facoltativa.

Dal **DeviceResources::CreateDeviceResources**:

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

Per supportare il rendering senza questa funzionalità facoltativa, l'app deve usare un geometry shader per impostare l'indice di matrice di destinazione di rendering. È necessario aggiungere questo frammento di codice *dopo aver* **VSSetConstantBuffers**, e *prima* **PSSetShader** nell'esempio di codice illustrato nella precedente sezione che illustra come eseguire il rendering stereo su HoloLens.

From **SpinningCubeRenderer::Render**:

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

**NOTA DI HLSL**: In questo caso, è necessario caricare un leggermente modificata vertex shader che passa l'indice di matrice di destinazione rendering di geometry shader usando un semantico, ad esempio TEXCOORD0 shader sempre consentito. Geometry shader non è necessario eseguire alcuna operazione; geometry shader modello passa attraverso tutti i dati, fatta eccezione per l'indice di matrice destinazione rendering, che consente di impostare il SV_RenderTargetArrayIndex semantico.

Codice del modello App per **GeometryShader.hlsl**:

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

## <a name="present"></a>Presente

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a>Abilitare il frame holographic presentare la catena di scambio

Con realtà mista di Windows, il sistema controlla la catena di scambio. Il sistema gestisce quindi i frame presentazione a ogni tipo di camera holographic per garantire un'esperienza utente di alta qualità. Fornisce inoltre un aggiornamento del riquadro di visualizzazione ogni fotogramma per ogni videocamera, per ottimizzare gli aspetti del sistema, ad esempio stabilizzazione immagine o acquisire realtà mista. Pertanto, non chiama un'app holographic usando DirectX **presente** su DXGI una catena di scambio. Usare invece i <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> classe per presentare tutte le catene di scambio per un frame dopo aver completato lo disegna.

Dal **DeviceResources::Present**:

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

Per impostazione predefinita, questa API è in attesa per il frame terminare prima che venga restituito. App holographic deve attendere per il frame precedente il completamento prima di iniziare a lavorare su un nuovo frame, perché questo riduce la latenza e consente per ottenere risultati migliori da stime holographic frame. Si tratta di una regola del disco rigida e se si dispone di frame che richiedono più di aggiornamento di una schermata per il rendering è possono disabilitare questo tipo di attesa, passando il parametro HolographicFramePresentWaitBehavior <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>. In questo caso, probabilmente si utilizzerebbe un thread di rendering asincrono per gestire un carico continuo sulla GPU. Si noti che la frequenza di aggiornamento del dispositivo HoloLens è 60hz, in cui un frame ha una durata pari a circa 16 ms. I dispositivi visore VR immersivi possono variare da 60hz a 90hz; Quando si aggiornano la visualizzazione 90 Hz, ogni fotogramma avranno una durata pari a circa 11 ms.

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a>Gestire gli scenari DeviceLost in collaborazione con il HolographicFrame

App DirectX 11 in genere è necessario controllare il valore HRESULT restituito dalla catena di scambio DXGI **presente** funzione per scoprire se si è verificato un **DeviceLost** errore. Il <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> classe a farlo. Esaminare i <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> restituisce per scoprire se è necessario rilasciare e ricreare il dispositivo Direct3D e le risorse basate sul dispositivo.

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

Si noti che se il dispositivo Direct3D persa e si ricrearlo, è necessario indicare il <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> per iniziare a usare il nuovo dispositivo. Verrà ricreata la catena di scambio per questo dispositivo.

From **DeviceResources::InitializeUsingHolographicSpace**:

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

Una volta che viene presentato il frame, è possibile tornare indietro al ciclo di programma principale e consentirgli di continuare al frame successivo.

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a>I PC grafica ibrida e le applicazioni di realtà mista

Windows 10 Creators Update PC può essere configurato con **entrambi** GPU discrete e integrate. Con questi tipi di computer, Windows sceglierà l'adapter a che di visore VR è connesso. Applicazioni devono assicurarsi che il dispositivo DirectX che crea Usa la stessa scheda.

Codice di esempio Direct3D più generale viene illustrata la creazione di un dispositivo DirectX usando la scheda hardware predefinito, che in un sistema ibrido potrebbe non essere identico a quello usato per le cuffie.

Per risolvere eventuali problemi di questo può causare, usare il <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> dalla <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>. PrimaryAdapterId() oppure <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>. AdapterId(). Questo adapterId è quindi utilizzabile per selezionare il giusto DXGIAdapter usando IDXGIFactory4.EnumAdapterByLuid.

From **DeviceResources::InitializeUsingHolographicSpace**:

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

Codice a **aggiornare DeviceResources::CreateDeviceResources aggiornerò IDXGIAdapter**

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

**Elementi grafici ibridi e Media Foundation**

Uso di Media Foundation in sistemi ibridi può causare problemi in cui non eseguirà il rendering video o video trama è danneggiata. Ciò può verificarsi perché Media Foundation è verrà utilizzato un comportamento del sistema come indicato in precedenza. In alcuni scenari, la creazione di un ID3D11Device separato è necessaria per il supporto multithreading e la creazione corretta flag sono impostati.

Durante l'inizializzazione di ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag deve essere definito come parte di D3D11_CREATE_DEVICE_FLAG. Dopo aver creato il dispositivo e il contesto, chiamare <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> per abilitare il multithreading. Per associare il dispositivo con il <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, utilizzare il <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> (funzione).

Codice a **associare un ID3D11Device IMFDXGIDeviceManager**:

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

## <a name="see-also"></a>Vedere anche
* [Sistemi di coordinate in DirectX](coordinate-systems-in-directx.md)
* [Uso dell'emulatore HoloLens](using-the-hololens-emulator.md)

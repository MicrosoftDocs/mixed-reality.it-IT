---
title: Creazione di un progetto di DirectX holographic
description: Viene illustrato come creare una nuova app holographic basata sul modello di app di realtà mista di Windows.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, app holographic, nuova app, app UWP, app per il modello, vntana, nuovo progetto, questa procedura dettagliata, download, esempi di codice
ms.openlocfilehash: a7eac9d8056fe5f7bcc442d6441f71331fa96cf6
ms.sourcegitcommit: 19c9bff21061d485821b61c9f3498daef8fa8235
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65828115"
---
# <a name="creating-a-holographic-directx-project"></a>Creazione di un progetto di DirectX holographic

Un'app holographic crei per un HoloLens sarà un <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">Universal Windows Platform (UWP) app</a>.  Se la destinazione auricolari realtà mista di Windows desktop, è possibile creare un'app UWP o un'applicazione Win32.

Il modello di app DirectX 11 holographic UWP è molto simile al modello di app DirectX 11 UWP. include un ciclo programma (o "ciclo del gioco"), un **DeviceResources** classe per gestire il dispositivo Direct3D e il contesto e una classe semplificata renderer di contenuto. Include anche un <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, analogamente a qualsiasi altra app UWP.

L'app di realtà mista, tuttavia, presenta alcune funzionalità aggiuntive che non sono presenti in un'app Direct3D 11 UWP tipica. Il modello di app per Windows Holographic è in grado di:
* Gestire le risorse dispositivo Direct3D associate fotocamere holographic.
* Recuperare i buffer nascosti fotocamera dal sistema.
* Gestire [estasiati](gaze.md) input e come riconoscere un semplice [movimento](gestures.md).
* Passare alla modalità di rendering stereo a schermo intero.

## <a name="how-do-i-get-started"></a>Come iniziare?

Primo [installare gli strumenti](install-the-tools.md), seguendo le istruzioni sul download di Visual Studio 2017 e l'emulatore di Microsoft HoloLens. I modelli di app holographic sono inclusi nel programma di installazione dell'emulatore di Microsoft HoloLens stesso. Assicurarsi anche che sia selezionata l'opzione per installare i modelli prima dell'installazione.

A questo punto è tutto pronto per creare l'app di realtà mista di Windows di DirectX 11. Si noti che per rimuovere il contenuto di esempio, impostare come commento il **DRAW_SAMPLE_CONTENT** direttiva del preprocessore in *PCH. h*.

## <a name="creating-a-uwp-project"></a>Crea un progetto UWP

Una volta il [gli strumenti vengono installati](install-the-tools.md) è quindi possibile creare un progetto UWP DirectX holographic.

Per creare un nuovo progetto:
1. Avviare **Visual Studio**.
2. Dal **File** dal menu **New** e selezionare **progetto** dal menu di scelta rapida. Il **nuovo progetto** verrà visualizzata la finestra di dialogo.
3. Espandere **Installed** a sinistra ed espandere le **Visual C++**  nodo relativo al linguaggio.
4. Passare il **universale di Windows > Holographic** nodo e selezionare **Holographic DirectX 11 App (Windows universale) (C++/WinRT)**.
   ![Screenshot della finestra di Holographic di DirectX 11 C++modello di progetto di app di WinRT UWP in Visual Studio](images/holographic-directx-app-cpp-new-project.png)<br>
   *Holographic DirectX 11 C++modello di progetto di app di WinRT UWP in Visual Studio*
   >[!IMPORTANT]
   >Assicurarsi che il nome del modello di progetto include "(C++/WinRT)".  In caso contrario, si dispone di una versione precedente dei modelli di progetto holographic installati.  Per ottenere modelli di progetto più recenti [installare l'emulatore di HoloLens più recente](using-the-hololens-emulator.md).
5. Immettere il **Name** e **posizione** caselle di testo e fare clic o toccare **OK**. Viene creato il progetto dell'app holographic.
6. Per lo sviluppo destinato a solo 2 HoloLens, assicurarsi che il **versione di destinazione** e **la versione minima** sono impostate su **Windows 10, versione 1903**.  Se la destinazione è HoloLens inoltre (1 ° generazione) o auricolari realtà mista di Windows desktop, è possibile impostare **la versione minima** a **Windows 10, versione 1809** invece, anche se questa operazione richiede alcuni <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank"> controlli adattivi delle versioni</a> nel codice quando si utilizzano nuove funzionalità di HoloLens 2.
   ![Screenshot dell'impostazione di Windows 10, versione 1903 come le versioni minima e di destinazione](images/new-uwp-project.png)<br>
   *L'impostazione **Windows 10, versione 1903** come le versioni minima e di destinazione*
   >[!IMPORTANT]
   >Se non viene visualizzata **Windows 10, versione 1903** come opzione, non è installato Windows 10 SDK più recente.  Per ottenere questa opzione vengano visualizzate <a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">installa versione 10.0.18362.0 o versioni successive di Windows 10 SDK</a>.

Il modello genera un progetto mediante <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, una proiezione di c++17 linguaggio C + + Runtime APIs Windows che supporta qualsiasi conforme agli standard C + + 17 del compilatore.  Il progetto viene illustrato come creare un cubo world-bloccato che ha inserito due contatori da parte dell'utente. L'utente può [-indice puntato](gestures.md#air-tap) o premere un pulsante sul controller per posizionare il cubo in una posizione diversa specificato dall'utente [estasiati](gaze.md). È possibile modificare il progetto per creare qualsiasi app di realtà mista.

In alternativa, è possibile creare un nuovo progetto usando il **Visual C#**  modello di progetto holographic, che si basa su SharpDX.  Se il holographic C# progetto non è stata avviata dal modello di app Windows Holographic, sarà necessario copiare il file ms.fxcompile.targets da una realtà mista di Windows C# modello di progetto e l'importazione nel file con estensione csproj del file per la compilazione HLSL file aggiunti al progetto.

Revisione [tramite Visual Studio per distribuire ed eseguire il debug](using-visual-studio.md) per informazioni su come compilare e distribuire l'esempio di HoloLens, un PC con immersiva dispositivo collegato o un emulatore.

Il resto di questa procedura presuppone che si sta utilizzando C++ per compilare l'app.

### <a name="uwp-app-entry-point"></a>Punto di ingresso di app UWP

Avvia l'app UWP holographic nel **wWinMain** funzione in AppView.cpp. Il **wWinMain** funzione crea l'app <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> e avvia il <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> con esso.

Dal **AppView.cpp**:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

Da quel momento, la classe AppView gestisce l'interazione con eventi di input di base di Windows, eventi CoreWindow e di messaggistica e così via. Verrà inoltre creato il HolographicSpace usati dall'app.

## <a name="creating-a-win32-project"></a>Creazione di un progetto Win32

Il modo più semplice per iniziare a compilare un Win32 holographic progetto consiste nell'adattare il <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram* esempio Win32</a>.

Questo esempio di Win32 viene utilizzata <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, una proiezione di c++17 linguaggio C + + Runtime APIs Windows che supporta qualsiasi conforme agli standard C + + 17 del compilatore.  Il progetto viene illustrato come creare un cubo world-bloccato che ha inserito due contatori da parte dell'utente. L'utente può premere un pulsante sul controller per posizionare il cubo in una posizione diversa specificato dall'utente [estasiati](gaze.md). È possibile modificare il progetto per creare qualsiasi app di realtà mista.

### <a name="win32-app-entry-point"></a>Punto di ingresso app Win32

Avvia l'app Win32 holographic nel **wWinMain** funzione in AppMain.cpp. Il **wWinMain** funzione crea HWND dell'app e avvia il ciclo di messaggi.

Dal **AppMain.cpp**:

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

Da quel momento, la classe AppMain gestisce l'interazione con i messaggi di finestre di base e così via. Verrà inoltre creato il HolographicSpace usati dall'app.

## <a name="render-holographic-content"></a>Il rendering del contenuto holographic

Il progetto **contenuti** cartella contiene le classi per vntana per il rendering nel [spazio holographic](getting-a-holographicspace.md). Ologramma l'impostazione predefinita nel modello è un cubo rotante che ha inserito due contatori lontano dall'utente. Disegno di questo cubo viene implementato in **SpinningCubeRenderer.cpp**, che dispone di questi metodi principali:

|  Metodo  |  Spiegazione | 
|----------|----------|
|  `CreateDeviceDependentResources` |  Carica gli shader e crea la rete mesh di cubo. | 
|  `PositionHologram` |  Inserisce l'ologrammi nella posizione specificata dall'oggetto <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>. | 
|  `Update` |  Ruota il cubo e imposta la matrice di modello. | 
|  `Render` |  Esegue il rendering di un frame utilizzando il vertex shader o pixel shader. | 

Il **shader** sottocartella contiene quattro implementazioni di shader predefinito:

|  Shader  |  Spiegazione | 
|----------|----------|
|  `GeometryShader.hlsl` |  Pass-through che lascia la geometria senza modificata. | 
|  `PixelShader.hlsl` |  Passaggi per i dati di colore. Dati relativi al colore sono interpolati e assegnati a un pixel in fase di rasterizzazione. | 
|  `VertexShader.hlsl` |  Shader semplice per eseguire l'elaborazione del vertice sulla GPU. | 
|  `VPRTVertexShader.hlsl` |  Shader semplice per eseguire l'elaborazione del vertice sulla GPU, che è ottimizzato per il rendering stereo realtà mista di Windows. | 

`VertexShaderShared.hlsl` contiene il codice comune condiviso tra `VertexShader.hlsl` e `VPRTVertexShader.hlsl`.

Gli shader vengono compilati quando viene compilato il progetto e caricati nel **SpinningCubeRenderer::CreateDeviceDependentResources** (metodo).

## <a name="interact-with-your-holograms"></a>Interagire con i vntana

Input dell'utente viene elaborata nel **SpatialInputHandler** classe, che viene una <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> dell'istanza e sottoscrive il <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> evento. Ciò consente di rilevare il movimento indice puntato e altri eventi di input spaziale.

## <a name="update-holographic-content"></a>Aggiornare il contenuto holographic

Gli aggiornamenti di app di realtà mista in un ciclo del gioco, che per impostazione predefinita viene implementato nel **Update** metodo `AppMain.cpp`. Il **Update** metodo aggiorna gli oggetti di scena, come il cubo rotante e restituisce un <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> oggetto usato per ottenere le matrici di visualizzazione e di proiezione aggiornate e per presentare la catena di scambio.

Il **eseguire il rendering** metodo nella `AppMain.cpp` accetta la <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> ed esegue il rendering il frame corrente a ogni tipo di camera holographic, in base all'app corrente e lo stato di posizionamento spaziale.

## <a name="see-also"></a>Vedere anche
* [Ottenere un HolographicSpace](getting-a-holographicspace.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [Rendering in DirectX](rendering-in-directx.md)
* [Uso di Visual Studio per distribuzione e debug](using-visual-studio.md)
* [Uso dell'emulatore HoloLens](using-the-hololens-emulator.md)
* [Uso di XAML con app DirectX olografiche](using-xaml-with-holographic-directx-apps.md)

---
title: Creazione di un progetto DirectX olografico
description: Viene illustrato come creare una nuova app olografica basata sul modello di app di realtà mista di Windows.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, app olografica, nuova app, app UWP, app modello, ologrammi, nuovo progetto, procedura dettagliata, download, codice di esempio
ms.openlocfilehash: 30f2c630b2919fbc304dc96d13cab74e22ed4adc
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277919"
---
# <a name="creating-a-holographic-directx-project"></a>Creazione di un progetto DirectX olografico

Un'app olografica creata per un HoloLens sarà un' <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">app piattaforma UWP (Universal Windows Platform) (UWP)</a>.  Se la destinazione è costituita da cuffie di realtà mista di Windows desktop, è possibile creare un'app UWP o un'app Win32.

Il modello di app UWP olografico DirectX 11 è molto simile al modello di app UWP di DirectX 11. include un ciclo di programma (o "ciclo di gioco"), una classe **DeviceResources** per gestire il dispositivo e il contesto Direct3D e una classe renderer di contenuto semplificata. Dispone anche di un <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, proprio come qualsiasi altra app UWP.

L'app per la realtà mista, tuttavia, presenta alcune funzionalità aggiuntive che non sono presenti in una tipica app UWP Direct3D. Il modello di app per la realtà mista di Windows è in grado di:
* Gestire le risorse del dispositivo Direct3D associate a fotocamere olografiche.
* Recuperare i buffer back della fotocamera dal sistema o, nel caso di Direct3D12, creare risorse buffer di back-out olografico e gestire la durata delle risorse.
* Gestire l'input di [sguardi](gaze-and-commit.md) e riconoscere un semplice [gesto](gaze-and-commit.md#composite-gestures).
* Passa alla modalità di rendering stereo a schermo intero.

## <a name="how-do-i-get-started"></a>Ricerca per categorie iniziare?

[Installare innanzitutto gli strumenti](install-the-tools.md)seguendo le istruzioni riportate in download di Visual Studio 2019 e dei modelli di app per la realtà mista di Windows. I modelli di app per la realtà mista sono disponibili in Visual Studio Marketplace come [download Web](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)oppure installarli come estensione tramite l'interfaccia utente di Visual Studio.

A questo punto si è pronti per creare l'app per la realtà mista di Windows DirectX 11. Si noti che per rimuovere il contenuto di esempio, impostare come commento la direttiva per il preprocessore **DRAW_SAMPLE_CONTENT** in *PCH. h*.

## <a name="creating-a-uwp-project"></a>Creazione di un progetto UWP

Una volta [installati gli strumenti](install-the-tools.md) , è possibile creare un progetto UWP DirectX olografico.

Per creare un nuovo progetto in Visual Studio 2019:
1. Avviare **Visual Studio**.
2. Nella sezione **Introduzione** a destra selezionare **Crea un nuovo progetto**.
3. Nei menu a discesa della finestra di dialogo **Crea un nuovo progetto** selezionare **C++** , **realtà mista di Windows**e **UWP**.
4. Selezionare l' **app olografica DirectX 11 (Windows universaleC++) (/WinRT)** .
   ![screenshot del modello di progetto app C++UWP olografico DirectX 11/WinRT in Visual Studio 2019](images/holographic-directx-app-cpp-new-project-2019.png)<br>
   *Modello di progetto C++di app UWP DirectX 11/WinRT olografico in Visual Studio 2019*
   >[!IMPORTANT]
   >Verificare che il nome del modello di progetto includa "C++(/WinRT)".  In caso contrario, è installata una versione precedente dei modelli di progetto olografici.  Per ottenere i modelli di progetto più recenti, [installarli](install-the-tools.md) come estensione di Visual Studio 2019.
5. Fare clic su **Avanti**.
5. Immettere le caselle di testo **nome progetto** e **percorso** e quindi fare clic o toccare **Crea**. Il progetto di app olografico viene creato.
6. Per lo sviluppo destinato solo a HoloLens 2, verificare che la versione di **destinazione** e la **versione minima** siano impostate su **Windows 10, versione 1903**.  Se si fa riferimento anche a HoloLens (1st Gen) o alle cuffie Desktop combinate di Windows desktop, è possibile impostare la **versione minima** su **Windows 10, versione 1809** , anche se questa operazione richiederà alcuni <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">controlli adattivi della versione</a> nel codice quando si usano le nuove funzionalità di HoloLens 2.
   ![screenshot dell'impostazione di Windows 10, versione 1903 come versione di destinazione e minima](images/new-uwp-project.png)<br>
   *Impostazione di **Windows 10, versione 1903** come versione di destinazione e minima*
   >[!IMPORTANT]
   >Se non viene visualizzata l'opzione **Windows 10, versione 1903** , non è installata la versione più recente di Windows 10 SDK.  Per visualizzare questa opzione, <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">installare la versione 10.0.18362.0 o successiva di Windows 10 SDK</a>.

Per creare un nuovo progetto in Visual Studio 2017:
1. Avviare **Visual Studio**.
2. Scegliere **nuovo** dal menu **file** e scegliere **progetto** dal menu di scelta rapida. Verrà visualizzata la finestra di dialogo **Nuovo progetto**.
3. Espandere **installato** a sinistra ed espandere il nodo **linguaggio C++ visuale** .
4. Passare al nodo **universale di Windows > olografico** e selezionare l' **app olografica DirectX 11 (WindowsC++universale) (/WinRT)** .
   ![screenshot del modello di progetto app C++UWP olografico DirectX 11/WinRT in Visual Studio 2017](images/holographic-directx-app-cpp-new-project.png)<br>
   *Modello di progetto C++di app UWP DirectX 11/WinRT olografico in Visual Studio 2017*
   >[!IMPORTANT]
   >Verificare che il nome del modello di progetto includa "C++(/WinRT)".  In caso contrario, è installata una versione precedente dei modelli di progetto olografici.  Per ottenere i modelli di progetto più recenti, [installarli](install-the-tools.md) come estensione di Visual Studio 2017.
5. Immettere le caselle di testo **nome** e **percorso** , quindi fare clic o toccare **OK**. Il progetto di app olografico viene creato.
6. Per lo sviluppo destinato solo a HoloLens 2, verificare che la versione di **destinazione** e la **versione minima** siano impostate su **Windows 10, versione 1903**.  Se si fa riferimento anche a HoloLens (1st Gen) o alle cuffie Desktop combinate di Windows desktop, è possibile impostare la **versione minima** su **Windows 10, versione 1809** , anche se questa operazione richiederà alcuni <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">controlli adattivi della versione</a> nel codice quando si usano le nuove funzionalità di HoloLens 2.
   ![screenshot dell'impostazione di Windows 10, versione 1903 come versione di destinazione e minima](images/new-uwp-project.png)<br>
   *Impostazione di **Windows 10, versione 1903** come versione di destinazione e minima*
   >[!IMPORTANT]
   >Se non viene visualizzata l'opzione **Windows 10, versione 1903** , non è installata la versione più recente di Windows 10 SDK.  Per visualizzare questa opzione, <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">installare la versione 10.0.18362.0 o successiva di Windows 10 SDK</a>.

Il modello genera un progetto con <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, una proiezione del linguaggio c++ 17 delle API Windows Runtime che supporta qualsiasi compilatore c++ 17 conforme agli standard.  Il progetto Mostra come creare un cubo con blocco globale posizionato a due metri dall'utente. L'utente può [toccare](gaze-and-commit.md#composite-gestures) o premere un pulsante sul controller per posizionare il cubo in una posizione diversa specificata dallo [sguardo](gaze-and-commit.md)dell'utente. È possibile modificare questo progetto per creare qualsiasi app di realtà mista.

In alternativa, è possibile creare un nuovo progetto usando il modello di progetto **Visual C#**  olografico, basato su SharpDX.  Se il progetto C# olografico non è stato avviato dal modello di applicazione olografica di Windows, sarà necessario copiare il file MS. fxcompile. targets da un C# progetto di modello di realtà mista di Windows e importarlo nel file con estensione csproj per compilare i file HLSL aggiunti al progetto. Un modello Direct3D 12 viene fornito anche nell'estensione modelli di app per la realtà mista di Windows in Visual Studio.

Vedere [uso di Visual Studio per distribuire ed eseguire il debug](using-visual-studio.md) per informazioni su come compilare e distribuire l'esempio in HOLOLENS, PC con dispositivo immersivo collegato o emulatore.

Nelle altre istruzioni riportate di seguito si presuppone che si C++ usi per compilare l'app.

### <a name="uwp-app-entry-point"></a>Punto di ingresso dell'app UWP

L'app UWP olografica viene avviata nella funzione **wWinMain** in AppView. cpp. La funzione **wWinMain** crea il <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> dell'app e avvia il <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> .

Da **AppView. cpp**:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

Da questo punto in poi, la classe AppView gestisce l'interazione con gli eventi di input di Windows Basic, gli eventi e la messaggistica CoreWindow e così via. Creerà anche il HolographicSpace usato dall'app.

## <a name="creating-a-win32-project"></a>Creazione di un progetto Win32

Il modo più semplice per iniziare a creare un progetto olografico Win32 consiste nell'adattare l' <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank">esempio Win32 *BasicHologram* </a>.

Questo esempio Win32 USA <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, una proiezione del linguaggio c++ 17 delle API Windows Runtime che supporta qualsiasi compilatore c++ 17 conforme agli standard.  Il progetto Mostra come creare un cubo con blocco globale posizionato a due metri dall'utente. L'utente può premere un pulsante sul controller per posizionare il cubo in una posizione diversa specificata dallo [sguardo](gaze-and-commit.md)dell'utente. È possibile modificare questo progetto per creare qualsiasi app di realtà mista.

### <a name="win32-app-entry-point"></a>Punto di ingresso dell'app Win32

L'app Win32 olografica viene avviata nella funzione **wWinMain** in AppMain. cpp. La funzione **wWinMain** crea l'oggetto HWND dell'app e avvia il ciclo di messaggi.

Da **AppMain. cpp**:

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

Da quel momento in poi, la classe AppMain gestisce l'interazione con i messaggi della finestra di base e così via. Creerà anche il HolographicSpace usato dall'app.

## <a name="render-holographic-content"></a>Rendering del contenuto olografico

La cartella **contenuto** del progetto contiene le classi per il rendering degli ologrammi nello [spazio olografico](getting-a-holographicspace.md). L'ologramma predefinito nel modello è un cubo rotante che è posizionata a due metri di fuori dall'utente. La creazione di questo cubo è implementata in **SpinningCubeRenderer. cpp**, che include i metodi principali seguenti:

|  Metodo  |  Spiegazione | 
|----------|----------|
|  `CreateDeviceDependentResources` |  Carica shader e crea la mesh del cubo. | 
|  `PositionHologram` |  Inserisce l'ologramma nella posizione specificata dal <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>fornito. | 
|  `Update` |  Ruota il cubo e imposta la matrice del modello. | 
|  `Render` |  Esegue il rendering di un frame utilizzando i vertici e i pixel shader. | 

La sottocartella **shader** contiene quattro implementazioni dello shader predefinite:

|  Shader  |  Spiegazione | 
|----------|----------|
|  `GeometryShader.hlsl` |  Un pass-through che lascia la geometria non modificata. | 
|  `PixelShader.hlsl` |  Passa i dati dei colori. I dati relativi ai colori vengono interpolati e assegnati a un pixel al passaggio di rasterizzazione. | 
|  `VertexShader.hlsl` |  Shader semplice per eseguire l'elaborazione del vertice sulla GPU. | 
|  `VPRTVertexShader.hlsl` |  Shader semplice per eseguire l'elaborazione dei vertici sulla GPU, ottimizzata per il rendering stereo di realtà mista di Windows. | 

`VertexShaderShared.hlsl` contiene codice comune condiviso tra `VertexShader.hlsl` e `VPRTVertexShader.hlsl`.

Nota: il modello di app Direct3D 12 include anche `ViewInstancingVertexShader.hlsl`. Questa variante usa le funzionalità facoltative di D3D12 per eseguire il rendering delle immagini stereo in modo più efficiente.

Gli shader vengono compilati al momento della compilazione del progetto e vengono caricati nel metodo **SpinningCubeRenderer:: CreateDeviceDependentResources** .

## <a name="interact-with-your-holograms"></a>Interagire con gli ologrammi

L'input dell'utente viene elaborato nella classe **SpatialInputHandler** , che ottiene un'istanza di <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> e sottoscrive l'evento <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> . In questo modo è possibile rilevare il movimento di tocco aereo e altri eventi di input spaziali.

## <a name="update-holographic-content"></a>Aggiorna contenuto olografico

Gli aggiornamenti dell'app di realtà mista in un ciclo di gioco, che per impostazione predefinita viene implementato nel metodo di **aggiornamento** in `AppMain.cpp`. Il metodo **Update** aggiorna gli oggetti della scena, ad esempio il cubo rotante, e restituisce un oggetto <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> usato per ottenere le matrici di visualizzazione e proiezione aggiornate e per presentare la catena di scambio.

Il metodo **Render** in `AppMain.cpp` accetta <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> ed esegue il rendering del frame corrente in ogni fotocamera olografica, in base all'app corrente e allo stato di posizionamento spaziale.

## <a name="notes"></a>Note

Il modello di app per la realtà mista di Windows supporta ora la compilazione con il flag di mitigazione Spectre abilitato (/Qspectre). Prima di compilare una configurazione con la mitigazione Spectre abilitata, assicurarsi C++ di installare le librerie di runtime di Microsoft Visual (MSVC) di Spectre. Per installare le C++ librerie di Spectre mitigate, avviare il programma di installazione di Visual Studio e selezionare **modifica**. Passare a **singoli componenti** e cercare "Spectre". Selezionare le caselle corrispondenti alle piattaforme di destinazione e alla versione di MSVC per cui è necessario compilare il codice con attenuazione Spectre per e fare clic su **modifica** per avviare l'installazione.

## <a name="see-also"></a>Vedere anche
* [Ottenere un HolographicSpace](getting-a-holographicspace.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [Rendering in DirectX](rendering-in-directx.md)
* [Uso di Visual Studio per distribuzione e debug](using-visual-studio.md)
* [Uso dell'emulatore HoloLens](using-the-hololens-emulator.md)
* [Uso di XAML con app DirectX olografiche](using-xaml-with-holographic-directx-apps.md)

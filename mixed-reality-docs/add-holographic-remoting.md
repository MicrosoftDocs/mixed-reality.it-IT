---
title: Aggiungere .NET remoting holographic
description: Viene illustrato come utilizzare i servizi remoti Holographic per il rendering vntana un HoloLens in rete.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, vntana, holographic .NET remoting, remoto per il rendering, rete per il rendering, HoloLens, vntana remoto
ms.openlocfilehash: 4726c6af43fe1b89fc8298e459a1af9dfa5fc667
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605129"
---
# <a name="add-holographic-remoting"></a>Aggiungere .NET remoting holographic

> [!NOTE]
> Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes).

## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>Aggiungere .NET remoting holographic a un'app UWP o il desktop

Questa pagina descrive come aggiungere Holographic .NET Remoting a un desktop o un'app UWP.

.NET remoting holographic consente all'app come destinazione un HoloLens con holographic contenuto ospitato in un PC desktop o in un dispositivo UWP, ad esempio Xbox One, consentendo l'accesso a più risorse di sistema e rendendo possibile l'integrazione remota [coinvolgenti visualizzazioni](app-views.md) nel software di PC desktop esistente. Un'applicazione host .NET remoting riceve un flusso di dati di input da un HoloLens, esegue il rendering di contenuto in una vista virtuale coinvolgente e trasmette i frame di contenuto a HoloLens. Viene stabilita la connessione tramite Wi-Fi standard. Per utilizzare .NET remoting, si verrà utilizzare un pacchetto NuGet per aggiungere remoting holographic a un'app UWP o il desktop e scrivere codice per gestire la connessione e per eseguire il rendering in una vista coinvolgente e concreto. Librerie di supporto sono inclusi nell'esempio di codice che consentono di semplificare l'attività di gestire la connessione al dispositivo.

Una connessione remota tipica avrà minimo a 50 ms di latenza. L'app di Windows Media player può segnalare la latenza in tempo reale.

>[!NOTE]
>I frammenti di codice in questo articolo illustrano attualmente l'utilizzo di C++/CX invece di C + + 17 conformi C++/WinRT usato nel [ C++ modello di progetto holographic](creating-a-holographic-directx-project.md).  I concetti sono equivalenti per un C++progetto /WinRT, anche se è necessario convertire il codice.

### <a name="get-the-remoting-nuget-packages"></a>Ottenere i pacchetti NuGet di .NET remoting

Seguire questi passaggi per ottenere il pacchetto NuGet per la comunicazione remota holographic e aggiungere un riferimento dal progetto:
1. Accedere al progetto in Visual Studio.
2. Fare doppio clic sul nodo del progetto e selezionare **Gestisci pacchetti NuGet...**
3. Nel pannello che viene visualizzata, fare clic su **esplorare** e quindi cercare "Holographic la comunicazione remota".
4. Selezionare **Microsoft.Holographic.Remoting** e fare clic su **installare**.
5. Se il **Preview** finestra di dialogo viene visualizzata, fare clic su **OK**.
6. Finestra di dialogo successiva visualizzata è il contratto di licenza. Fare clic su **accetto** per accettare il contratto di licenza.

### <a name="create-the-holographicstreamerhelpers"></a>Creare il HolographicStreamerHelpers

In primo luogo, è necessaria un'istanza di HolographicStreamerHelpers. Aggiungere questo elemento alla classe che gestiscono i servizi remoti.

```
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

È inoltre necessario tenere traccia dello stato di connessione. Se si desidera eseguire il rendering di anteprima, è necessario disporre di una trama da copiare. Anche necessario alcuni aspetti, ad esempio un blocco dello stato di connessione, un modo per archiviare l'indirizzo IP di HoloLens e così via.

```
private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::SRWLock                   m_connectionStateLock;

       RemotingHostSample::AppView^                        m_appView;
       Platform::String^                                   m_ipAddress;
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::CriticalSection           m_deviceLock;
       Microsoft::WRL::ComPtr<IDXGISwapChain1>             m_swapChain;
       Microsoft::WRL::ComPtr<ID3D11Texture2D>             m_spTexture;
```

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>Inizializzare HolographicStreamerHelpers e connettersi a HoloLens

Per connettersi a un dispositivo HoloLens, creare un'istanza di HolographicStreamerHelpers e connettersi all'indirizzo IP di destinazione. È necessario impostare le dimensioni del fotogramma video in modo che corrisponda la larghezza di visualizzazione di HoloLens e l'altezza, in quanto la libreria .NET Remoting Holographic prevede che il codificatore e decodificatore risoluzioni in modo che corrisponda esattamente.

```
m_streamerHelpers = ref new HolographicStreamerHelpers();
       m_streamerHelpers->CreateStreamer(m_d3dDevice);

       // We currently need to stream at 720p because that's the resolution of our remote display.
       // There is a check in the holographic streamer that makes sure the remote and local
       // resolutions match. The default streamer resolution is 1080p.
       m_streamerHelpers->SetVideoFrameSize(1280, 720);

       try
       {
           m_streamerHelpers->Connect(m_ipAddress->Data(), 8001);
       }
       catch (Platform::Exception^ ex)
       {
           DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
       }
```

La connessione del dispositivo è asincrona. Le esigenze delle app per fornire i gestori eventi per connettersi, disconnettersi e frame di inviare eventi.

L'evento OnConnected può aggiornare l'interfaccia utente, avvio del rendering e così via. Nel nostro esempio di codice per il desktop, è aggiornare il titolo della finestra con un messaggio di "connessione".

```
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

Può gestire l'evento OnDisconnected riconnessione, aggiornamenti dell'interfaccia utente e così via. In questo esempio è ristabilire la connessione se si verifica un errore temporaneo.

```
Platform::WeakReference streamerHelpersWeakRef = Platform::WeakReference(m_streamerHelpers);
       m_streamerHelpers->OnDisconnected += ref new DisconnectedEvent(
           [this, streamerHelpersWeakRef](_In_ HolographicStreamerConnectionFailureReason failureReason)
           {
               DebugLog(L"Disconnected with reason %d", failureReason);
               UpdateWindowTitle();

               // Reconnect if this is a transient failure.
               if (failureReason == HolographicStreamerConnectionFailureReason::Unreachable ||
                   failureReason == HolographicStreamerConnectionFailureReason::ConnectionLost)
               {
                   DebugLog(L"Reconnecting...");

                   try
                   {
                       auto helpersResolved = streamerHelpersWeakRef.Resolve<HolographicStreamerHelpers>();
                       if (helpersResolved)
                       {
                           helpersResolved->Connect(m_ipAddress->Data(), 8001);
                       }
                       else
                       {
                           DebugLog(L"Failed to reconnect because a disconnect has already occurred.\n");
                       }
                   }
                   catch (Platform::Exception^ ex)
                   {
                       DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
                   }
               }
               else
               {
                   DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
               }
           });
```

Quando il componente di .NET remoting è pronto per l'invio di un frame, l'app viene fornita un'opportunità per creare una copia di esso nel SendFrameEvent. In questo caso, deve essere copiato il frame di una catena di scambio in modo che è possibile visualizzarla in una finestra di anteprima.

```
m_streamerHelpers->OnSendFrame += ref new SendFrameEvent(
           [this](_In_ const ComPtr<ID3D11Texture2D>& spTexture, _In_ FrameMetadata metadata)
           {
               if (m_showPreview)
               {
                   ComPtr<ID3D11Device1> spDevice = m_appView->GetDeviceResources()->GetD3DDevice();
                   ComPtr<ID3D11DeviceContext> spContext = m_appView->GetDeviceResources()->GetD3DDeviceContext();

                   ComPtr<ID3D11Texture2D> spBackBuffer;
                   ThrowIfFailed(m_swapChain->GetBuffer(0, IID_PPV_ARGS(&spBackBuffer)));

                   spContext->CopySubresourceRegion(
                       spBackBuffer.Get(), // dest
                       0,                  // dest subresource
                       0, 0, 0,            // dest x, y, z
                       spTexture.Get(),    // source
                       0,                  // source subresource
                       nullptr);           // source box, null means the entire resource

                   DXGI_PRESENT_PARAMETERS parameters = { 0 };
                   ThrowIfFailed(m_swapChain->Present1(1, 0, &parameters));
               }
           });
```

### <a name="render-holographic-content"></a>Il rendering del contenuto holographic

Per eseguire il rendering del contenuto tramite la comunicazione remota, si imposta una IFrameworkView virtuale all'interno di un'app UWP o il desktop ed elaborare holographic frame da servizi remoti .NET. Tutte le API di Windows Holographic sono Usa che esattamente da questa visualizzazione, ma è configurato in modo leggermente diverso.

Anziché crearne di nuove autonomamente, i componenti dello spazio e riconoscimento vocale holographic provengono dalla classe HolographicRemotingHelpers:

```
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

Invece di usare un ciclo di aggiornamento all'interno di un metodo di esecuzione, è fornire gli aggiornamenti dei segni di graduazione dal ciclo principale del desktop o dell'app UWP. In questo modo il desktop o app UWP per rimanere in controllo dell'elaborazione del messaggio.

```
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

Metodo Tick() della visualizzazione olografica app completa un'iterazione dell'aggiornamento, draw, ciclo presenta.

```
void AppView::Tick()
   {
       if (m_main)
       {
           // When running on Windows Holographic, we can use the holographic rendering system.
           HolographicFrame^ holographicFrame = m_main->Update();

           if (holographicFrame && m_main->Render(holographicFrame))
           {
               // The holographic frame has an API that presents the swap chain for each
               // holographic camera.
               m_deviceResources->Present(holographicFrame);
           }
       }
   }
```

L'aggiornamento della visualizzazione olografica app, rendering e ciclo presenta è esattamente lo stesso di quando in esecuzione su HoloLens - ad eccezione del fatto che si ha accesso a una maggiore quantità di risorse di sistema nel PC desktop. È possibile eseguire il rendering di molte altre triangoli, avere ulteriori passaggi di disegni, eseguire ulteriori fisica e usano x64 processi per caricare il contenuto che richiede più di 2 GB di RAM.

### <a name="disconnect-and-end-the-remote-session"></a>Disconnettersi e terminare la sessione remota

Per disconnettere - ad esempio, quando l'utente sceglie un pulsante di interfaccia utente di disconnettere - chiamare Disconnect () sul HolographicStreamerHelpers e infine rilasciare l'oggetto.

```
void DesktopWindow::DisconnectFromRemoteDevice()
   {
       // Disconnecting from the remote device can change the connection state.
       auto exclusiveLock = m_connectionStateLock.LockExclusive();

       if (m_streamerHelpers != nullptr)
       {
           m_streamerHelpers->Disconnect();

           // Reset state
           m_streamerHelpers = nullptr;
       }
   }
```

## <a name="get-the-remoting-player"></a>Ottenere il lettore di servizi remoti

L'assegnatario di comunicazione remota di Windows Holographic è disponibile in app store di Windows come endpoint per la comunicazione remota di hosting di App a cui connettersi. Per ottenere l'assegnatario di comunicazione remota di Windows Holographic, visitare l'app di Windows store da di HoloLens, ricerca per la comunicazione remota e scaricare l'app. Il giocatore remoto include una funzionalità per visualizzare le statistiche su schermo, che può essere utile durante il debug di .NET remoting hosting delle app.

## <a name="notes-and-resources"></a>Note e le risorse

La visualizzazione olografica app sarà necessario un modo per fornire all'app con il dispositivo Direct3D, che deve essere utilizzato per inizializzare lo spazio holographic. L'app deve usare questo dispositivo Direct3D per copiare e visualizzare il frame di anteprima.

```
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**Esempio di codice:** Un esempio di codice .NET Remoting Holographic completo è disponibile, che include una visualizzazione olografica applicazione compatibile con .NET remoting e di host .NET remoting per desktop Win32, DirectX UWP e UWP con XAML. Per ottenerlo, fare clic qui:
* [Esempio di codice Holographic Windows per la comunicazione remota](https://github.com/Microsoft/HoloLensCompanionKit/)

**Nota di debug:** La libreria .NET Remoting Holographic può generare eccezioni first-chance. Queste eccezioni possono essere visibili nella sessione, a seconda delle impostazioni di eccezione di Visual Studio attivi al momento di debug. Queste eccezioni vengono intercettate internamente dalla libreria di .NET Remoting Holographic e possono essere ignorate.

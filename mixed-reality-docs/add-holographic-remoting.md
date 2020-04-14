---
title: Aggiungere la comunicazione remota olografica
description: Viene illustrato come usare la comunicazione remota olografica per eseguire il rendering degli ologrammi in una HoloLens in rete.
author: mikeriches
ms.author: mriches
ms.date: 05/24/2019
ms.topic: article
keywords: Realtà mista di Windows, ologrammi, comunicazione remota olografica, rendering remoto, rendering di rete, HoloLens, ologrammi remoti
ms.openlocfilehash: 2f6ade5552c993f66281d0be8a7e62c8f076deac
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277709"
---
# <a name="add-holographic-remoting-hololens-1st-gen"></a>Aggiungere la comunicazione remota olografica (HoloLens (1st Gen))

>[!IMPORTANT]
>Questo documento descrive la creazione di un'applicazione host per HoloLens 1. L'applicazione host per **HoloLens (1st Gen)** deve usare il pacchetto NuGet versione **1. x. x**. Ciò implica che le applicazioni host scritte per HoloLens 1 non sono compatibili con HoloLens 2 e viceversa.

## <a name="hololens-2"></a>HoloLens 2

Gli sviluppatori HoloLens che usano la comunicazione remota olografica dovranno aggiornare le proprie app per renderle compatibili con HoloLens 2. Questa operazione richiede una nuova versione del pacchetto NuGet di comunicazione remota olografica. Se un'applicazione che usa il pacchetto NuGet di comunicazione remota olografica con un numero di versione inferiore a 2.0.0.0 tenta di connettersi al lettore di comunicazione remota olografica in HoloLens 2, la connessione avrà esito negativo.

>[!NOTE]
>Le linee guida specifiche per HoloLens 2 sono disponibili [qui](holographic-remoting-create-host.md).


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>Aggiungere la comunicazione remota olografica all'app desktop o UWP

Questa pagina descrive come aggiungere la comunicazione remota olografica a un'app desktop o UWP.

La comunicazione remota olografica consente all'app di avere come destinazione un HoloLens con contenuto olografico ospitato in un computer desktop o in un dispositivo UWP come Xbox One, consentendo l'accesso a più risorse di sistema e rendendo possibile l'integrazione di [visualizzazioni immersive](app-views.md) remote in software per PC desktop esistenti. Un'app host Remoting riceve un flusso di dati di input da un HoloLens, esegue il rendering del contenuto in una visualizzazione immersiva virtuale e trasmette i frame di contenuto a HoloLens. La connessione viene eseguita usando il Wi-Fi standard. Per usare la comunicazione remota, si userà un pacchetto NuGet per aggiungere la comunicazione remota olografica all'app desktop o UWP e scrivere il codice per gestire la connessione e per eseguire il rendering in una visualizzazione immersiva. Le librerie helper sono incluse nell'esempio di codice che semplificano l'attività di gestione della connessione del dispositivo.

Una tipica connessione remota avrà una bassa di 50 ms di latenza. L'App Player può segnalare la latenza in tempo reale.

>[!NOTE]
>I frammenti di codice in questo articolo illustrano attualmente l' C++uso di/CX, invece di/WinRT conformi C++a C + 17 come usato nel modello di [ C++ progetto olografico](creating-a-holographic-directx-project.md).  I concetti sono equivalenti per C++un progetto/WinRT, anche se sarà necessario tradurre il codice.

### <a name="get-the-remoting-nuget-packages"></a>Ottenere i pacchetti NuGet per la comunicazione remota

Seguire questa procedura per ottenere il pacchetto NuGet per la comunicazione remota olografica e aggiungere un riferimento dal progetto:
1. Passare al progetto in Visual Studio.
2. Fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Gestisci pacchetti NuGet...**
3. Nel pannello visualizzato fare clic su **Sfoglia** e quindi cercare "comunicazione remota olografica".
4. Selezionare **Microsoft. olografic. Remoting** e fare clic su **Installa**.
5. Se viene visualizzata la finestra di dialogo **Anteprima** , fare clic su **OK**.
6. La finestra di dialogo successiva visualizzata è il contratto di licenza. Fare clic su **Accetto** per accettare il contratto di licenza.

### <a name="create-the-holographicstreamerhelpers"></a>Creare il HolographicStreamerHelpers

In primo luogo, è necessaria un'istanza di HolographicStreamerHelpers. Aggiungere questo oggetto alla classe che gestirà la comunicazione remota.

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

Sarà inoltre necessario tenere traccia dello stato della connessione. Se si desidera eseguire il rendering dell'anteprima, è necessario disporre di una trama in cui copiarla. Sono necessari anche alcuni elementi, ad esempio un blocco dello stato della connessione, un modo per archiviare l'indirizzo IP di HoloLens e così via.

```cpp
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

Per connettersi a un dispositivo HoloLens, creare un'istanza di HolographicStreamerHelpers e connettersi all'indirizzo IP di destinazione. È necessario impostare la dimensione del fotogramma video in modo che corrisponda alla larghezza e all'altezza di visualizzazione HoloLens, perché la libreria remota olografica prevede che le risoluzioni del codificatore e del decodificatore corrispondano esattamente.

```cpp
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

La connessione del dispositivo è asincrona. L'app deve fornire gestori eventi per gli eventi di connessione, disconnessione e invio frame.

L'evento OnConnected può aggiornare l'interfaccia utente, avviare il rendering e così via. Nell'esempio di codice desktop, viene aggiornato il titolo della finestra con un messaggio "Connected".

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

L'evento disconnected può gestire la riconnessione, gli aggiornamenti dell'interfaccia utente e così via. In questo esempio viene riconnessa se si verifica un errore temporaneo.

```cpp
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

Quando il componente remoto è pronto per l'invio di un frame, l'app ha la possibilità di crearne una copia nella SendFrameEvent. Qui viene copiato il frame in una catena di scambio in modo che sia possibile visualizzarlo in una finestra di anteprima.

```cpp
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

### <a name="render-holographic-content"></a>Rendering del contenuto olografico

Per eseguire il rendering del contenuto usando la comunicazione remota, è necessario configurare un IFrameworkView virtuale all'interno dell'app desktop o UWP ed elaborare i frame olografici dalla comunicazione remota. Tutte le API olografiche di Windows vengono utilizzate allo stesso modo da questa visualizzazione, ma sono impostate in modo leggermente diverso.

Invece di crearli autonomamente, i componenti di spazio olografico e vocale provengono dalla classe HolographicRemotingHelpers:

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

Anziché usare un ciclo di aggiornamento all'interno di un metodo Run, è necessario fornire gli aggiornamenti del ciclo principale dell'app desktop o UWP. Ciò consente all'app desktop o UWP di rimanere in controllo dell'elaborazione dei messaggi.

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

Il metodo di sequenza () del segno di visualizzazione dell'app olografica completa un'iterazione del ciclo di aggiornamento, di estrazione e di presentazione.

```cpp
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

Il ciclo di aggiornamento, rendering e presenza dell'app olografica è identico a quello che si verifica quando è in esecuzione in HoloLens, ad eccezione del fatto che è possibile accedere a una quantità molto maggiore di risorse di sistema nel PC desktop. È possibile eseguire il rendering di molti più triangoli, avere più passaggi di disegno, eseguire più fisica e usare processi x64 per caricare contenuti che richiedono più di 2 GB di RAM.

### <a name="disconnect-and-end-the-remote-session"></a>Disconnetti e termina la sessione remota

Per disconnettersi, ad esempio, quando l'utente fa clic su un pulsante dell'interfaccia utente per disconnettere-chiamare Disconnect () in HolographicStreamerHelpers e quindi rilasciare l'oggetto.

```cpp
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

## <a name="get-the-remoting-player"></a>Ottenere il lettore di comunicazione remota

Il lettore di comunicazione remota olografica di Windows è disponibile nell'App Store di Windows come endpoint per le applicazioni host Remote a cui connettersi. Per ottenere il lettore di comunicazione remota olografica Windows, visitare l'App Store di Windows dalla HoloLens, cercare i servizi remoti e scaricare l'app. Il lettore .NET Remoting include una funzionalità per la visualizzazione delle statistiche sullo schermo, che può essere utile quando si esegue il debug di applicazioni host Remote.

## <a name="notes-and-resources"></a>Note e risorse

La visualizzazione dell'app olografica richiede un modo per fornire all'app il dispositivo Direct3D, che deve essere usato per inizializzare lo spazio olografico. L'app deve usare questo dispositivo Direct3D per copiare e visualizzare il frame di anteprima.

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**Esempio di codice:** È disponibile un esempio di codice .NET Remoting completo, che include una visualizzazione di applicazioni olografica compatibile con i progetti host .NET Remoting e Remoting per desktop Win32, UWP DirectX e UWP con XAML. Per ottenerlo, fare clic qui:
* [Esempio di codice Windows olografico per servizi remoti](https://github.com/Microsoft/HoloLensCompanionKit/)

**Nota di debug:** La libreria remota olografica può generare eccezioni first-chance. Queste eccezioni possono essere visibili nelle sessioni di debug, a seconda delle impostazioni delle eccezioni di Visual Studio attive al momento. Queste eccezioni vengono rilevate internamente dalla libreria di comunicazione remota olografica e possono essere ignorate.

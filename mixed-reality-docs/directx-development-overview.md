---
title: Panoramica sullo sviluppo nativo
description: Creare un motore di realtà mista basato su DirectX usando direttamente le API di realtà mista di Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX, rendering olografico, nativo, app nativa, WinRT, app WinRT, API della piattaforma, motore personalizzato, middleware
ms.openlocfilehash: 5c61739ea6c90b4547c5c9927cf2129304650926
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80159997"
---
# <a name="native-development-overview"></a>Panoramica sullo sviluppo nativo

Le applicazioni di realtà mista di Windows usano le API seguenti per creare esperienze di [realtà mista](mixed-reality.md) per HoloLens e altri auricolari immersivi:

 - [Rendering olografico](rendering.md)
 - [Sguardo fisso](gaze-and-commit.md)
 - [Gesto](gaze-and-commit.md#composite-gestures)
 - [Controller di movimento](motion-controllers.md)
 - [Voce](voice-input.md)
 - [Mapping spaziale](spatial-mapping.md)

È possibile creare applicazioni con realtà mista usando un motore 3D, ad esempio [Unity](unity-development-overview.md). In alternativa, è possibile scrivere codice direttamente nelle API di realtà mista di Windows usando DirectX 11 o DirectX 12. Se si usa direttamente la piattaforma, si crea essenzialmente un middleware o un Framework personalizzato. Le API di Windows supportano le applicazioni scritte sia C++ in che C#in. Se si usa C#, l'applicazione può sfruttare la libreria software open source [SharpDX](https://sharpdx.org/) .

La realtà mista [di Windows supporta due tipi di app](app-views.md):
* **Applicazioni a realtà mista** (UWP o Win32) che usano l'API [HOLOGRAPHICSPACE](getting-a-holographicspace.md) o l' [API OpenXR](openxr.md) per eseguire il rendering di una [visualizzazione immersiva](app-views.md) per l'utente che riempie la visualizzazione dell'auricolare
* **app 2D** (UWP) che usano DirectX, XAML o un altro Framework per eseguire il rendering di [visualizzazioni 2D](app-views.md#2d-views) in slate nella Home realtà mista di Windows

Le differenze tra lo sviluppo di DirectX per le [visualizzazioni 2D e le visualizzazioni immersive](app-views.md) riguardano principalmente il rendering olografico e l'input spaziale. Il [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) dell'applicazione UWP o l'HWND dell'applicazione Win32 sono obbligatori e rimangono in gran parte uguali. Lo stesso vale per le API WinRT disponibili per l'app. È tuttavia necessario usare un subset diverso di queste API per sfruttare le funzionalità olografiche. Ad esempio, presentazione catena e frame presenti vengono gestiti dal sistema per le applicazioni olografiche allo scopo di abilitare un ciclo di frame stimato per la posa.

## <a name="get-started-with-openxr"></a>Introduzione a OpenXR

È possibile sviluppare usando OpenXR in un headset HoloLens 2 o Windows Mixed Reality immersive sul desktop.  Se non si ha accesso a una cuffia, è invece possibile usare l'emulatore HoloLens 2 o il simulatore di realtà mista di Windows.

Per iniziare a sviluppare applicazioni OpenXR per HoloLens 2 o cuffie di realtà miste Windows immersive, vedere [come iniziare a usare lo sviluppo OpenXR](openxr-getting-started.md).

## <a name="get-started-with-winrt"></a>Introduzione a WinRT

Per iniziare a sviluppare applicazioni immersive:
* Per le **app UWP**, [usare i modelli in Visual Studio per creare un nuovo progetto UWP](creating-a-holographic-directx-project.md). In base al linguaggio, al C++ Visual o C#all'oggetto visivo, trovare i modelli UWP in **Windows Universal** > **olografic**.
* Per **le applicazioni Win32**, [iniziare dall'esempio Win32 *BasicHologram* ](creating-a-holographic-directx-project.md#creating-a-win32-project).

Questo passaggio è un ottimo modo per ottenere il codice necessario per aggiungere il supporto per il rendering olografico a un'applicazione o a un motore esistente. Il codice e i concetti vengono presentati nel modello in modo che sia familiare a tutti gli sviluppatori di software interattivo in tempo reale.

Gli argomenti seguenti descrivono i requisiti di base quando si aggiunge il supporto della realtà mista di Windows al middleware basato su DirectX.

* [Creare un progetto DirectX olografico](creating-a-holographic-directx-project.md): il modello di applicazione olografico associato alla documentazione Mostra le differenze rispetto a quello che si sta usando. Vengono inoltre descritti i requisiti speciali per un dispositivo progettato per funzionare durante il riposo.
* [Ottenere un HolographicSpace](getting-a-holographicspace.md): prima di tutto è necessario creare un HolographicSpace che fornisca all'applicazione la sequenza di oggetti HolographicFrame che rappresentano ogni posizione Head da cui verrà eseguito il rendering.
* [Rendering in DirectX](rendering-in-directx.md): poiché un presentazione catena olografico ha due destinazioni di rendering, è necessario apportare alcune modifiche al modo in cui viene eseguito il rendering dell'app.
* [Sistemi di coordinate in DirectX](coordinate-systems-in-directx.md): la realtà mista di Windows apprende e aggiorna la comprensione del mondo quando l'utente si aggira. In questo modo vengono forniti i sistemi di coordinate spaziali usati dalle applicazioni per ragionare sull'ambiente dell'utente, inclusi i ancoraggi spaziali e la fase spaziale definita dall'utente.

## <a name="add-mixed-reality-capabilities-and-inputs"></a>Aggiungere funzionalità e input di realtà mista

Per fornire la migliore esperienza possibile per gli utenti dell'app immersiva, è necessario supportare i blocchi predefiniti seguenti:

* [Puntamento con la testa e sguardo fisso in DirectX](gaze-in-directx.md)
* [Mani e controller del movimento in DirectX](hands-and-motion-controllers-in-directx.md)
* [Input vocale in DirectX](voice-input-in-directx.md)
* [Audio spaziale](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)
* [Mapping spaziale in DirectX](spatial-mapping-in-directx.md)

Si tratta di altre funzionalità chiave usate da molte applicazioni immersive che sono esposte anche a applicazioni DirectX:

* [Ancoraggi nello spazio condivisi in DirectX](shared-spatial-anchors-in-directx.md)
* [Input da tastiera, mouse e controller in DirectX](keyboard-mouse-and-controller-input-in-directx.md)

## <a name="see-also"></a>Vedere anche
* [Modello di app](app-model.md)
* [Visualizzazioni delle app](app-views.md)

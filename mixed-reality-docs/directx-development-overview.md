---
title: Panoramica dello sviluppo DirectX
description: Creazione di un motore di realtà mista basati su DirectX usando direttamente le API di realtà mista di Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX, holographic il rendering, native app native, WinRT, WinRT app, le API della piattaforma, motore personalizzato, middleware
ms.openlocfilehash: da6beae6e256fef49481b581395e507b3f2acd04
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414377"
---
# <a name="directx-development-overview"></a>Panoramica dello sviluppo DirectX


Le applicazioni di realtà mista di Windows usare il [rendering holographic](rendering.md), [estasiati](gaze.md), [movimento](gestures.md), [controller movimento](motion-controllers.md), [vocali](voice-input.md), e [mapping spaziale](spatial-mapping.md) le API per compilare [realtà mista](mixed-reality.md) esperienze per HoloLens e auricolari coinvolgente e concreto. È possibile creare usando un motore 3D, come le applicazioni di realtà mista [Unity](unity-development-overview.md), oppure è possibile immettere direttamente il codice per le API di realtà mista di Windows usando DirectX 11 o DirectX 12. Se si stanno sfruttando la piattaforma direttamente, essenzialmente creando il proprio middleware o framework. Le API di Windows supportano le applicazioni scritte sia in C++ e C#. Se si sceglie di usare C#, l'applicazione può sfruttare il [SharpDX](http://sharpdx.org/) libreria di software open source.


Realtà mista di Windows supporta [due tipi di app](app-views.md):
* **Applicazioni di realtà mista** (UWP o Win32) che usano i [HolographicSpace API](getting-a-holographicspace.md) per eseguire il rendering un [vista coinvolgente](app-views.md) all'utente che riempie la visualizzazione visore Vr.
* **Le app 2D** (UWP) che usano altri Framework, XAML o DirectX per eseguire il rendering [visualizzazioni 2D](app-views.md#2d-views) sul Tablet in casa la realtà mista di Windows.


Le differenze tra lo sviluppo per DirectX [visualizzazioni 2D e coinvolgenti visualizzazioni](app-views.md) sono principalmente correlate a holographic per il rendering e input spaziale. Dell'applicazione UWP [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) o HWND dell'applicazione Win32 sono necessari e in larga misura rimangono invariate, così come le APIs WinRT disponibili per l'applicazione. Tuttavia, è necessario utilizzare un diverso subset di queste API per sfruttare i vantaggi delle funzionalità holographic. Ad esempio, la catena di scambio è gestita dal sistema per appslications holographic. Si lavora con l'API HolographicSpace anziché DXGI per [presentare frame](rendering-in-directx.md).

Per iniziare lo sviluppo di applicazioni immersive:
* Per la **le app UWP**, [creare un nuovo progetto UWP usando i modelli in Visual Studio](creating-a-holographic-directx-project.md). Base del linguaggio **Visual C++**  oppure **Visual C#** , è possibile trovare i modelli UWP in **universale di Windows**  >   **Holographic**.
* Per la **applicazioni Win32**, [avviare dal *BasicHologram* esempio Win32](creating-a-holographic-directx-project.md#creating-a-win32-project).

Questo è un ottimo modo per ottenere il codice che è necessario aggiungere il supporto per il rendering holographic a un'applicazione o un motore esistente. Nel modello in modo familiare per gli sviluppatori di software interattivo in tempo reale vengono presentati i concetti e codice.


## <a name="getting-started"></a>Attività iniziali

Gli argomenti seguenti descrivono i requisiti di base dell'aggiunta del supporto di realtà mista di Windows basata su DirectX middleware:

* [Creazione di un progetto di DirectX holographic](creating-a-holographic-directx-project.md): Il modello di applicazione holographic accoppiato con la documentazione illustra le differenze tra quella usata per nonché i requisiti speciali introdotti da un dispositivo che è progettato per funzionare al tempo stesso posizionando l'inizio.
* [Ottenere un HolographicSpace](getting-a-holographicspace.md): È innanzitutto necessario creare un HolographicSpace che fornirà all'applicazione la sequenza di oggetti HolographicFrame che rappresentano ogni head posizione da cui è possibile eseguire il rendering.
* [Il rendering in DirectX](rendering-in-directx.md): Poiché una catena di scambio holographic dispone di due destinazioni di rendering, è necessario apportare alcune modifiche al modo in cui viene eseguito il rendering dell'applicazione.
* [Sistemi di coordinate in DirectX](coordinate-systems-in-directx.md): Realtà mista di Windows rileva e aggiorna la comprensione del mondo come l'utente scorre attorno a. In questo modo spaziali sistemi di coordinate che le applicazioni utilizzano per prendere in considerazione automobilista dell'utente, inclusi gli ancoraggi spaziali e l'utente definito fase spaziale.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Aggiunta di input e le funzionalità di realtà mista

Per abilitare la migliore esperienza possibile per gli utenti delle appslication coinvolgenti, è necessario supportare i blocchi predefiniti principali seguenti:

* [Puntamento con la testa e sguardo fisso in DirectX](gaze-in-directx.md)
* [Mani e controller del movimento in DirectX](hands-and-motion-controllers-in-directx.md)
* [Input vocale in DirectX](voice-input-in-directx.md)
* [Audio spaziale in DirectX](spatial-sound-in-directx.md)
* [Mapping spaziale in DirectX](spatial-mapping-in-directx.md)


Sono disponibili altre funzionalità chiave che dovranno utilizzare molte applicazioni coinvolgenti che vengono anche esposti ad applicazioni DirectX:

* [Ancoraggi nello spazio condivisi in DirectX](shared-spatial-anchors-in-directx.md)
* [Fotocamera individuabile in DirectX](locatable-camera-in-directx.md)
* [Input da tastiera, mouse e controller in DirectX](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>Vedere anche
* [Modello di app](app-model.md)
* [Visualizzazioni delle app](app-views.md)

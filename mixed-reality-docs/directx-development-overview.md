---
title: Panoramica dello sviluppo DirectX
description: Creazione di un motore di realtà mista basati su DirectX usando direttamente le API di realtà mista di Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX, holographic il rendering, native app native, WinRT, WinRT app, le API della piattaforma, motore personalizzato, middleware
ms.openlocfilehash: 60c4de7025099f38f0902e2ff24579e7088835a6
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65628982"
---
# <a name="directx-development-overview"></a>Panoramica dello sviluppo DirectX

Usare le app di realtà mista di Windows il [rendering holographic](rendering.md), [estasiati](gaze.md), [movimento](gestures.md), [controller movimento](motion-controllers.md), [vocale ](voice-input.md) e [mapping spaziale](spatial-mapping.md) le API per compilare [realtà mista](mixed-reality.md) esperienze per HoloLens e auricolari coinvolgente e concreto. È possibile creare usando un motore 3D, ad esempio le app di realtà mista [Unity](unity-development-overview.md), oppure è possibile immettere direttamente il codice per le API di realtà mista di Windows usando DirectX 11 o DirectX 12. Se si stanno sfruttando la piattaforma direttamente, essenzialmente creando il proprio middleware o framework. Le API di Windows supportano le app scritte sia in C++ e C#. Se si desidera utilizzare C#, l'applicazione può sfruttare il [SharpDX](http://sharpdx.org/) libreria di software open source.

Realtà mista di Windows supporta [due tipi di app](app-views.md):
* **Le App per realtà mista** (UWP o Win32), che usano i [HolographicSpace API](getting-a-holographicspace.md) per eseguire il rendering un [visualizzazione coinvolgenti](app-views.md) all'utente che riempie la visualizzazione visore Vr.
* **Le app 2D** (UWP), che usa DirectX, XAML o altri framework per eseguire il rendering [visualizzazioni 2D](app-views.md#2d-views) sul Tablet in casa la realtà mista di Windows.

Le differenze tra lo sviluppo per DirectX [visualizzazioni 2D e coinvolgenti visualizzazioni](app-views.md) sono principalmente correlate a holographic per il rendering e input spaziale. Dell'app UWP [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) o HWND dell'app Win32 siano ancora necessari e in larga misura rimangono invariate, così come le APIs WinRT disponibile per l'app. È tuttavia possibile utilizzare un diverso subset di queste API per sfruttare i vantaggi delle funzionalità holographic. Ad esempio, la catena di scambio è gestita dal sistema per le app holographic e si lavora con l'API HolographicSpace anziché DXGI per [presentare frame](rendering-in-directx.md).

Per iniziare lo sviluppo di App immersive:
* Per la **le app UWP**, [creare un nuovo progetto UWP usando i modelli in Visual Studio](creating-a-holographic-directx-project.md). La lingua, in base **Visual C++**  oppure **Visual C#** , si troverà i modelli UWP in **universale di Windows**  >   **Holographic**.
* Per la **App Win32**, [avviare dal *BasicHologram* esempio Win32](creating-a-holographic-directx-project.md#creating-a-win32-project).

Questo è un ottimo modo per ottenere il codice che è necessario aggiungere supporto per il rendering holographic a un'app o un motore esistente. Nel modello in modo familiare per gli sviluppatori di software interattivo in tempo reale vengono presentati i concetti e codice.

## <a name="getting-started"></a>Attività iniziali

Gli argomenti seguenti descrivono i requisiti di base dell'aggiunta del supporto di realtà mista di Windows basata su DirectX middleware:
* [Creazione di un progetto di DirectX holographic](creating-a-holographic-directx-project.md): Il modello di app holographic accoppiato con la documentazione illustra le differenze tra ciò che è possibile usare e i requisiti speciali introdotti da un dispositivo che è progettato per funzionare al tempo stesso posizionando l'inizio.
* [Ottenere un HolographicSpace](getting-a-holographicspace.md): È innanzitutto necessario creare un HolographicSpace, in modo da fornire all'app la sequenza di oggetti HolographicFrame che rappresentano ogni head posizione da cui è possibile eseguire il rendering.
* [Il rendering in DirectX](rendering-in-directx.md): Poiché una catena di scambio holographic dispone di due destinazioni di rendering, è probabilmente necessario apportare alcune modifiche al modo in cui viene eseguito il rendering dell'applicazione.
* [Sistemi di coordinate in DirectX](coordinate-systems-in-directx.md): Realtà mista di Windows rileva e aggiorna la comprensione del mondo come si interromperanno l'utente, fornendo spaziali sistemi di coordinate che usano le App per prendere in considerazione automobilista dell'utente, inclusi gli ancoraggi spaziali e fase spaziali definita dell'utente.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Aggiunta di input e le funzionalità di realtà mista

Per abilitare la migliore esperienza possibile per gli utenti delle App immersive, è necessario supportare i blocchi predefiniti principali seguenti:
* [Testa e occhio estasiati DirectX](gaze-in-directx.md)
* [Le mani e i controller di movimento in DirectX](hands-and-motion-controllers-in-directx.md)
* [Input vocale in DirectX](voice-input-in-directx.md)
* [Audio spaziale in DirectX](spatial-sound-in-directx.md)
* [Mapping spaziale in DirectX](spatial-mapping-in-directx.md)

Sono disponibili altre funzionalità chiave che molte applicazioni coinvolgenti dovranno usare, che vengono esposte anche ad App DirectX:
* [Ancoraggi nello spazio condivisi in DirectX](shared-spatial-anchors-in-directx.md)
* [Fotocamera individuabile in DirectX](locatable-camera-in-directx.md)
* [Input da tastiera, mouse e controller in DirectX](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>Vedere anche
* [Modello di app](app-model.md)
* [Visualizzazioni delle app](app-views.md)

---
title: Panoramica sullo sviluppo di DirectX
description: Creazione di un motore di realtà mista basato su DirectX usando direttamente le API di realtà mista di Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX, rendering olografico, nativo, app nativa, WinRT, app WinRT, API della piattaforma, motore personalizzato, middleware
ms.openlocfilehash: 58b311038633dc325cc2c5425fd09b9a0192b161
ms.sourcegitcommit: 4ac761fed7a9570977f6d031ba4f870585d6630a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68861699"
---
# <a name="directx-development-overview"></a>Panoramica sullo sviluppo di DirectX


Le applicazioni di realtà mista di Windows usano le API di [rendering olografico](rendering.md), [sguardi](gaze.md), [movimenti](gestures.md), [controller di movimento](motion-controllers.md), [voce](voice-input.md)e [mapping spaziale](spatial-mapping.md) per creare esperienze di [realtà miste](mixed-reality.md) per HoloLens e auricolari immersivi. È possibile creare applicazioni con realtà mista usando un motore 3D, ad esempio [Unity](unity-development-overview.md), oppure è possibile scrivere direttamente codice per le API di realtà mista di Windows usando DirectX 11 o DirectX 12. Se si usa direttamente la piattaforma, sarà essenzialmente necessario creare un middleware o un Framework personalizzato. Le API di Windows supportano le applicazioni scritte C++ sia C#in che in. Se si sceglie di usare C#, l'applicazione può sfruttare la libreria software open source [SharpDX](http://sharpdx.org/) .


La realtà mista [di Windows supporta due tipi di app](app-views.md):
* **Applicazioni di realtà mista** (UWP o Win32) che usano l' [API HolographicSpace](getting-a-holographicspace.md) per eseguire il rendering di una [visualizzazione immersiva](app-views.md) per l'utente che riempie la visualizzazione dell'auricolare.
* **app 2D** (UWP) che usano DirectX, XAML o altri Framework per eseguire il rendering di [visualizzazioni 2D](app-views.md#2d-views) in slate nella Home realtà mista di Windows.


Le differenze tra lo sviluppo di DirectX per le visualizzazioni [2D e le visualizzazioni immersive](app-views.md) sono correlate principalmente al rendering olografico e all'input spaziale. Il [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) dell'applicazione UWP o l'HWND dell'applicazione Win32 sono necessari e rimangono in gran parte uguali, come le API WinRT disponibili per l'applicazione. Tuttavia, è necessario usare un subset diverso di queste API per sfruttare le funzionalità olografiche. Ad esempio, la catena di scambio viene gestita dal sistema per appslications olografici. Si lavora con l'API HolographicSpace anziché con DXGI per [presentare i frame](rendering-in-directx.md).

Per iniziare a sviluppare applicazioni immersive:
* Per le **app UWP**, [creare un nuovo progetto UWP usando i modelli in Visual Studio](creating-a-holographic-directx-project.md). In base al linguaggio, all'oggetto **visivo C++**  o all'oggetto **visivo C#** , è possibile trovare i modelli UWP in **Universal** > **olografico**di Windows.
* Per **le applicazioni Win32**, [iniziare dall'esempio Win32 *BasicHologram* ](creating-a-holographic-directx-project.md#creating-a-win32-project).

Questo è un ottimo modo per ottenere il codice necessario per aggiungere il supporto per il rendering olografico a un'applicazione o a un motore esistente. Il codice e i concetti vengono presentati nel modello in modo che sia familiare a tutti gli sviluppatori di software interattivo in tempo reale.


## <a name="getting-started"></a>Introduzione

Negli argomenti seguenti vengono illustrati i requisiti di base per l'aggiunta del supporto per la realtà mista di Windows al middleware basato su DirectX:

* [Creazione di un progetto DirectX olografico](creating-a-holographic-directx-project.md): Il modello di applicazione olografica abbinato alla documentazione Mostra le differenze tra quello che si sta usando e i requisiti speciali introdotti da un dispositivo progettato per funzionare mentre si è in testa.
* [Recupero di un HolographicSpace](getting-a-holographicspace.md): Sarà prima di tutto necessario creare un HolographicSpace che fornisca all'applicazione la sequenza di oggetti HolographicFrame che rappresentano ogni posizione Head da cui verrà eseguito il rendering.
* [Rendering in DirectX](rendering-in-directx.md): Poiché una catena di scambio olografica ha due destinazioni di rendering, è necessario apportare alcune modifiche al modo in cui viene eseguito il rendering dell'applicazione.
* [Sistemi di coordinate in DirectX](coordinate-systems-in-directx.md): La realtà mista di Windows apprende e aggiorna la propria comprensione del mondo quando l'utente si aggira. In questo modo vengono forniti i sistemi di coordinate spaziali usati dalle applicazioni per ragionare sull'ambiente dell'utente, inclusi i ancoraggi spaziali e la fase spaziale definita dall'utente.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Aggiunta di input e funzionalità di realtà mista

Per abilitare la migliore esperienza possibile per gli utenti della appslication immersiva, è necessario supportare i blocchi predefiniti seguenti:

* [Puntamento con la testa e sguardo fisso in DirectX](gaze-in-directx.md)
* [Mani e controller del movimento in DirectX](hands-and-motion-controllers-in-directx.md)
* [Input vocale in DirectX](voice-input-in-directx.md)
* [Audio spaziale in DirectX](spatial-sound-in-directx.md)
* [Mapping spaziale in DirectX](spatial-mapping-in-directx.md)


Sono disponibili altre funzionalità chiave che molte applicazioni immersive utilizzeranno anche per le applicazioni DirectX:

* [Ancoraggi nello spazio condivisi in DirectX](shared-spatial-anchors-in-directx.md)
* [Input da tastiera, mouse e controller in DirectX](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>Vedere anche
* [Modello di app](app-model.md)
* [Visualizzazioni delle app](app-views.md)

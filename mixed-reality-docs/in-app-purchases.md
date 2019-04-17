---
title: Acquisti in-app
description: Acquisti in-app sono supportati nelle app di realtà mista, ma ha richiesto alcune operazioni per la loro configurazione.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: acquisti in-app, hololens
ms.openlocfilehash: bc96893d1777e94295285736982fd9a7167240a4
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602882"
---
# <a name="in-app-purchases"></a><span data-ttu-id="adc5c-104">Acquisti in-app</span><span class="sxs-lookup"><span data-stu-id="adc5c-104">In-app purchases</span></span>

<span data-ttu-id="adc5c-105">Acquisti in-app sono supportati in HoloLens, ma ha richiesto alcune operazioni per la loro configurazione.</span><span class="sxs-lookup"><span data-stu-id="adc5c-105">In-app purchases are supported in HoloLens, but there is some work to set them up.</span></span>

<span data-ttu-id="adc5c-106">Per sfruttare l'acquisto di app in funzionalità, è necessario:</span><span class="sxs-lookup"><span data-stu-id="adc5c-106">In order to leverage the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="adc5c-107">Creare un XAML [visualizzazione 2D](app-views.md) venga visualizzato come uno slate</span><span class="sxs-lookup"><span data-stu-id="adc5c-107">Create a XAML [2D view](app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="adc5c-108">Passare a esso per attivare la selezione host, che lascia la visualizzazione coinvolgente</span><span class="sxs-lookup"><span data-stu-id="adc5c-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="adc5c-109">Chiamare l'API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="adc5c-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="adc5c-110">Questa API attiverà il popup del sistema operativo Windows azionario che mostra il nome di acquisto in-app, descrizione e prezzo.</span><span class="sxs-lookup"><span data-stu-id="adc5c-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="adc5c-111">L'utente può quindi scegliere le opzioni di acquisto.</span><span class="sxs-lookup"><span data-stu-id="adc5c-111">The user can then choose purchase options.</span></span> <span data-ttu-id="adc5c-112">Una volta completata l'azione, l'app dovrà disporre dell'interfaccia utente che consente all'utente di tornare al relativo [vista coinvolgente](app-views.md).</span><span class="sxs-lookup"><span data-stu-id="adc5c-112">Once the action is completed, the app will need to present UI which allows the user to switch back to its [immersive view](app-views.md).</span></span>

<span data-ttu-id="adc5c-113">Per le app destinate a auricolari immersive realtà mista di Windows basata su desktop, non è necessario passare manualmente a una visualizzazione XAML prima di chiamare l'API RequestProductPurchaseAsync.</span><span class="sxs-lookup"><span data-stu-id="adc5c-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it is not required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>

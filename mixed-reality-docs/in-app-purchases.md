---
title: Acquisti in-app
description: Gli acquisti in-app sono supportati nelle app per realtà mista, ma è necessario configurarli.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: acquisti in-app, hololens
ms.openlocfilehash: bc96893d1777e94295285736982fd9a7167240a4
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515299"
---
# <a name="in-app-purchases"></a><span data-ttu-id="11585-104">Acquisti in-app</span><span class="sxs-lookup"><span data-stu-id="11585-104">In-app purchases</span></span>

<span data-ttu-id="11585-105">Gli acquisti in-app sono supportati in HoloLens, ma è necessario configurarli.</span><span class="sxs-lookup"><span data-stu-id="11585-105">In-app purchases are supported in HoloLens, but there is some work to set them up.</span></span>

<span data-ttu-id="11585-106">Per sfruttare le funzionalità di acquisto di app, è necessario:</span><span class="sxs-lookup"><span data-stu-id="11585-106">In order to leverage the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="11585-107">Creare una [visualizzazione 2D](app-views.md) XAML da visualizzare come ardesia</span><span class="sxs-lookup"><span data-stu-id="11585-107">Create a XAML [2D view](app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="11585-108">Passare ad esso per attivare la selezione host, che lascia la visualizzazione immersiva</span><span class="sxs-lookup"><span data-stu-id="11585-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="11585-109">Chiamare l'API: await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="11585-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="11585-110">Questa API visualizzerà il popup del sistema operativo Windows azionario che mostra il nome, la descrizione e il prezzo dell'acquisto in-app.</span><span class="sxs-lookup"><span data-stu-id="11585-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="11585-111">L'utente può quindi scegliere le opzioni di acquisto.</span><span class="sxs-lookup"><span data-stu-id="11585-111">The user can then choose purchase options.</span></span> <span data-ttu-id="11585-112">Al termine dell'azione, l'app deve presentare l'interfaccia utente che consente all'utente di tornare alla [visualizzazione immersiva](app-views.md).</span><span class="sxs-lookup"><span data-stu-id="11585-112">Once the action is completed, the app will need to present UI which allows the user to switch back to its [immersive view](app-views.md).</span></span>

<span data-ttu-id="11585-113">Per le app destinate a auricolari di Windows a realtà mista basate su desktop, non è necessario passare manualmente a una visualizzazione XAML prima di chiamare l'API RequestProductPurchaseAsync.</span><span class="sxs-lookup"><span data-stu-id="11585-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it is not required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>

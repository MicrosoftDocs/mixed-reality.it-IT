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
# <a name="in-app-purchases"></a>Acquisti in-app

Acquisti in-app sono supportati in HoloLens, ma ha richiesto alcune operazioni per la loro configurazione.

Per sfruttare l'acquisto di app in funzionalità, è necessario:
* Creare un XAML [visualizzazione 2D](app-views.md) venga visualizzato come uno slate
* Passare a esso per attivare la selezione host, che lascia la visualizzazione coinvolgente
* Chiamare l'API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

Questa API attiverà il popup del sistema operativo Windows azionario che mostra il nome di acquisto in-app, descrizione e prezzo. L'utente può quindi scegliere le opzioni di acquisto. Una volta completata l'azione, l'app dovrà disporre dell'interfaccia utente che consente all'utente di tornare al relativo [vista coinvolgente](app-views.md).

Per le app destinate a auricolari immersive realtà mista di Windows basata su desktop, non è necessario passare manualmente a una visualizzazione XAML prima di chiamare l'API RequestProductPurchaseAsync.

---
title: Esperienze condivise in Unity
description: Condividere la stessa vntana tra più utenti in un'applicazione Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Sharing, Anchor, WorldAnchor, MR Sharing 250, WorldAnchorTransferBatch, SpatialPerception, Azure, Azure Spatial Anchors, ASA
ms.openlocfilehash: fe755c15d942660b1e16b2335db28d3d7ce72816
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605070"
---
# <a name="shared-experiences-in-unity"></a>Esperienze condivise in Unity

Un'esperienza condivisa è un dove più utenti, ognuno con i propri HoloLens, dispositivo iOS o Android, collettivamente consente di visualizzare e interagiscono con lo stesso ologrammi cui sono posizionato in corrispondenza di un punto fisso nello spazio. Questa operazione viene eseguita tramite la condivisione di ancoraggio spaziale.

## <a name="azure-spatial-anchors"></a>Ancoraggio spaziale di Azure

È possibile usare <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Anchor spaziali Azure</a> creare durevole supportata da cloud spaziali ancoraggi, che consente quindi di individuare l'app in più HoloLens, dispositivi iOS e Android.  Condividendo un ancoraggio spaziale comune tra più dispositivi, ogni utente può visualizzare il contenuto sottoposto a rendering relativo tale ancoraggio nella stessa posizione fisica.  Ciò consente esperienze condivise in tempo reale.

È anche possibile usare <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Anchor spaziali Azure</a> per la persistenza asincrona ologrammi nei dispositivi Android, iOS e HoloLens.  Condividendo un ancoraggio spaziali cloud durevole, più dispositivi possono osservare le stessi ologrammi persistenti nel corso del tempo, anche se questi dispositivi non sono presenti nello stesso momento.

Per iniziare a creare esperienze condivise in Unity, provare i 5 minuti <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guide introduttive di Azure spaziali Anchor Unity</a>.

Quando si è in esecuzione con Azure Anchor spaziale, è possibile quindi <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">creare e individuare gli ancoraggi in Unity</a>.

## <a name="local-anchor-transfers"></a>Trasferimenti di ancoraggio locale

In situazioni in cui non è possibile usare Azure spaziali gli ancoraggi, [trasferimenti di ancoraggio locale](local-anchor-transfers-in-unity.md) abilitare un dispositivo HoloLens esportare un ancoraggio per essere importati da un secondo dispositivo HoloLens.  Si noti che questo approccio offre richiamo ancoraggio meno affidabile rispetto a Azure spaziali ancoraggi e dispositivi iOS e Android non sono supportati da questo approccio.

## <a name="see-also"></a>Vedere anche
* [Condividere esperienze in realtà mista](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Anchor spaziali</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Ancoraggi spaziali Azure SDK per Unity</a>
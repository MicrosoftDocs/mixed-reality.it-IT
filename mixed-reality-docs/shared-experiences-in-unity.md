---
title: Esperienze condivise in Unity
description: Condividere gli stessi ologrammi tra più utenti in un'applicazione Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Condivisione, ancoraggio, WorldAnchor, MR sharing 250, WorldAnchorTransferBatch, SpatialPerception, Azure, ancoraggi spaziali di Azure, ASA
ms.openlocfilehash: fe755c15d942660b1e16b2335db28d3d7ce72816
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516798"
---
# <a name="shared-experiences-in-unity"></a>Esperienze condivise in Unity

Un'esperienza condivisa è quella in cui più utenti, ognuno con il proprio dispositivo HoloLens, iOS o Android, visualizzano collettivamente e interagiscono con lo stesso ologramma posizionato in un punto fisso nello spazio. Questa operazione viene eseguita tramite la condivisione di ancoraggio spaziale.

## <a name="azure-spatial-anchors"></a>Ancoraggio spaziale di Azure

È possibile usare gli <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">ancoraggi spaziali di Azure</a> per creare ancoraggi spaziali durevoli basati sul cloud, che possono essere individuati dall'app su più dispositivi HoloLens, iOS e Android.  Condividendo un ancoraggio spaziale comune tra più dispositivi, ogni utente può visualizzare il contenuto di cui è stato eseguito il rendering relativo a tale ancoraggio nella stessa posizione fisica.  Ciò rende possibili esperienze condivise in tempo reale.

Puoi usare <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello spazio di Azure</a> anche per la persistenza asincrona degli ologrammi su dispositivi HoloLens, iOS e Android.  Condividendo un ancoraggio durevole nello spazio del cloud, più dispositivi possono osservare nel tempo lo stesso ologramma salvato in modo permanente, anche se tali dispositivi non sono presenti insieme contemporaneamente.

Per iniziare a creare esperienze condivise in Unity, provare le <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guide introduttive Unity Anchors di Azure</a>di 5 minuti.

Quando si è operativi con i Anchor spaziali di Azure, è possibile <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">creare e individuare ancoraggi in Unity</a>.

## <a name="local-anchor-transfers"></a>Trasferimenti di ancoraggio locali

Nei casi in cui non è possibile usare gli ancoraggi spaziali di Azure, i [trasferimenti di ancoraggio locali](local-anchor-transfers-in-unity.md) consentono a un dispositivo HoloLens di esportare un ancoraggio per l'importazione da parte di un secondo dispositivo HoloLens.  Si noti che questo approccio offre un richiamo di ancoraggio meno affidabile rispetto agli ancoraggi spaziali di Azure e i dispositivi iOS e Android non sono supportati da questo approccio.

## <a name="see-also"></a>Vedere anche
* [Esperienze condivise nella realtà mista](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK per Unity</a>
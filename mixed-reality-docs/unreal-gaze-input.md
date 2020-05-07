---
title: Input di sguardi in Unreal
description: Spiega come usare l'input di sguardi in Unreal
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Realtà mista di Windows, ologrammi, HoloLens, rilevamento degli occhi
ms.openlocfilehash: 7387bb3f25cdbdfac32f508c173fbd098f844e84
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835625"
---
# <a name="gaze-input"></a>Input sguardo

Il plug-in realtà mista di Windows non fornisce funzioni speciali per l'input dello sguardo. Tutto funziona anche se l'API standard non reale.

[API sguardo a capo](https://docs.unrealengine.com/en-US/BlueprintAPI/Input/HeadMountedDisplay/index.html)

## <a name="eye-tracking"></a>Tracciamento oculare

Per usare l'API di rilevamento degli occhi, gli sviluppatori devono abilitare la funzionalità di "input dello sguardo" nelle impostazioni del progetto HoloLens. All'avvio dell'applicazione, l'utente visualizzerà la richiesta di consenso seguente

![Autorizzazioni di input per gli occhi](images/unreal/eye-input-permissions.png)
 
Se l'utente concede l'autorizzazione, l'applicazione riceverà un input con sguardo. 

L'API di rilevamento degli occhi di Unreal è documentata [qui](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html)

I dettagli tecnici della verifica degli occhi sono disponibili [qui](eye-tracking.md)

Si noti che, in particolare, per il rilevamento degli occhi di HoloLens è presente un singolo raggio di sguardi per entrambi gli occhi. HoloLens non offre la traccia stereoscopica degli occhi.

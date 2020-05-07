---
title: Input vocale
description: Spiega come usare l'input vocale
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Realtà mista di Windows, HoloLens
ms.openlocfilehash: d61a9f9d40c76c8872ff0a1b39d65f95ae88d2b7
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835315"
---
# <a name="voice-input"></a>Input vocale

Per abilitare il riconoscimento vocale in HoloLens, lo sviluppatore deve abilitare "Microphone" nell'editor Unreal in Project Settings > Platform > HoloLens > capabilities. Il dispositivo deve avere anche il riconoscimento vocale abilitato in impostazioni > privacy > vocale e usare la lingua inglese.

![Impostazioni di riconoscimento vocale Windows](images/unreal/speech-recognition-settings.png)

È consigliabile abilitare il riconoscimento vocale in linea anche per la migliore qualità possibile del servizio. I dettagli tecnici per il riconoscimento vocale in HoloLens sono disponibili [qui](voice-input.md)

Quindi, l'utente visualizzerà una finestra di dialogo in cui viene abilitato il microfono all'avvio iniziale dell'applicazione. Se un utente seleziona Sì, l'applicazione inizierà a ricevere l'input vocale.

L'input vocale non richiede un'API di realtà mista di Windows speciale ed è invece basato sull'API di mapping di input di Unreal Engine 4 esistente. Per informazioni dettagliate su come usare l'API di input, vedere [qui](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html)

I mapping vocale sono stati aggiunti alla sezione Bindings del motore-input sotto l'azione e i mapping degli assi. 

![Setttings input motore UE4](images/unreal/engine-input.png)
 
Di seguito è riportato un esempio di monitoraggio aggiuntivo per il mondo "Jump". È possibile utilizzare qualsiasi parola o frase breve in lingua inglese. 

Dopo l'aggiunta di un mapping vocale tramite le impostazioni del progetto, uno sviluppatore può usare la logica standard Unreal per gestire l'input, come nell'esempio seguente: 
 
![Azione semplice per la voce](images/unreal/input-action-bp.png)

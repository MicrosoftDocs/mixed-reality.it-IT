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
# <a name="voice-input"></a><span data-ttu-id="7b8d1-104">Input vocale</span><span class="sxs-lookup"><span data-stu-id="7b8d1-104">Voice Input</span></span>

<span data-ttu-id="7b8d1-105">Per abilitare il riconoscimento vocale in HoloLens, lo sviluppatore deve abilitare "Microphone" nell'editor Unreal in Project Settings > Platform > HoloLens > capabilities.</span><span class="sxs-lookup"><span data-stu-id="7b8d1-105">To enable speech recognition on HoloLens, the developer needs to enable “Microphone” in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span> <span data-ttu-id="7b8d1-106">Il dispositivo deve avere anche il riconoscimento vocale abilitato in impostazioni > privacy > vocale e usare la lingua inglese.</span><span class="sxs-lookup"><span data-stu-id="7b8d1-106">The device must also have Speech recognition enabled in Settings > Privacy > Speech and use the English language.</span></span>

![Impostazioni di riconoscimento vocale Windows](images/unreal/speech-recognition-settings.png)

<span data-ttu-id="7b8d1-108">È consigliabile abilitare il riconoscimento vocale in linea anche per la migliore qualità possibile del servizio.</span><span class="sxs-lookup"><span data-stu-id="7b8d1-108">It’s recommended to enable Online speech recognition too for the best possible quality of the service.</span></span> <span data-ttu-id="7b8d1-109">I dettagli tecnici per il riconoscimento vocale in HoloLens sono disponibili [qui](voice-input.md)</span><span class="sxs-lookup"><span data-stu-id="7b8d1-109">Technical details for speech recognition on HoloLens can be found [here](voice-input.md)</span></span>

<span data-ttu-id="7b8d1-110">Quindi, l'utente visualizzerà una finestra di dialogo in cui viene abilitato il microfono all'avvio iniziale dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="7b8d1-110">Then user will see a dialog about enabling the microphone when the application first starts.</span></span> <span data-ttu-id="7b8d1-111">Se un utente seleziona Sì, l'applicazione inizierà a ricevere l'input vocale.</span><span class="sxs-lookup"><span data-stu-id="7b8d1-111">If a user selects Yes, the application will begin getting voice input.</span></span>

<span data-ttu-id="7b8d1-112">L'input vocale non richiede un'API di realtà mista di Windows speciale ed è invece basato sull'API di mapping di input di Unreal Engine 4 esistente.</span><span class="sxs-lookup"><span data-stu-id="7b8d1-112">Speech input doesn’t require a special Windows Mixed Reality API and is instead built upon the existing Unreal Engine 4 Input mapping API.</span></span> <span data-ttu-id="7b8d1-113">Per informazioni dettagliate su come usare l'API di input, vedere [qui](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html)</span><span class="sxs-lookup"><span data-stu-id="7b8d1-113">Details on how to use the Input API are [here](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html)</span></span>

<span data-ttu-id="7b8d1-114">I mapping vocale sono stati aggiunti alla sezione Bindings del motore-input sotto l'azione e i mapping degli assi.</span><span class="sxs-lookup"><span data-stu-id="7b8d1-114">Speech Mappings have been added to the Bindings section of Engine – Input below Action and Axis Mappings.</span></span> 

![Setttings input motore UE4](images/unreal/engine-input.png)
 
<span data-ttu-id="7b8d1-116">Di seguito è riportato un esempio di monitoraggio aggiuntivo per il mondo "Jump".</span><span class="sxs-lookup"><span data-stu-id="7b8d1-116">Here is an example of added monitoring for the world “jump”.</span></span> <span data-ttu-id="7b8d1-117">È possibile utilizzare qualsiasi parola o frase breve in lingua inglese.</span><span class="sxs-lookup"><span data-stu-id="7b8d1-117">Any English word(s) or short sentences can be used.</span></span> 

<span data-ttu-id="7b8d1-118">Dopo l'aggiunta di un mapping vocale tramite le impostazioni del progetto, uno sviluppatore può usare la logica standard Unreal per gestire l'input, come nell'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="7b8d1-118">After a Speech Mapping is added via Project Settings, a developer can then use standard Unreal logic to handle the input, as in the following example:</span></span> 
 
![Azione semplice per la voce](images/unreal/input-action-bp.png)

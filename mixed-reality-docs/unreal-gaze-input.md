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
# <a name="gaze-input"></a><span data-ttu-id="27e80-104">Input sguardo</span><span class="sxs-lookup"><span data-stu-id="27e80-104">Gaze Input</span></span>

<span data-ttu-id="27e80-105">Il plug-in realtà mista di Windows non fornisce funzioni speciali per l'input dello sguardo.</span><span class="sxs-lookup"><span data-stu-id="27e80-105">The Windows Mixed Reality plugin doesn’t provide any special functions for the gaze input.</span></span> <span data-ttu-id="27e80-106">Tutto funziona anche se l'API standard non reale.</span><span class="sxs-lookup"><span data-stu-id="27e80-106">Everything works though the standard Unreal API.</span></span>

[<span data-ttu-id="27e80-107">API sguardo a capo</span><span class="sxs-lookup"><span data-stu-id="27e80-107">Head gaze API</span></span>](https://docs.unrealengine.com/en-US/BlueprintAPI/Input/HeadMountedDisplay/index.html)

## <a name="eye-tracking"></a><span data-ttu-id="27e80-108">Tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="27e80-108">Eye tracking</span></span>

<span data-ttu-id="27e80-109">Per usare l'API di rilevamento degli occhi, gli sviluppatori devono abilitare la funzionalità di "input dello sguardo" nelle impostazioni del progetto HoloLens.</span><span class="sxs-lookup"><span data-stu-id="27e80-109">To use the eye tracking API, developers should enable the “Gaze Input” capability in their HoloLens project settings.</span></span> <span data-ttu-id="27e80-110">All'avvio dell'applicazione, l'utente visualizzerà la richiesta di consenso seguente</span><span class="sxs-lookup"><span data-stu-id="27e80-110">When the application starts, user will see the following consent prompt</span></span>

![Autorizzazioni di input per gli occhi](images/unreal/eye-input-permissions.png)
 
<span data-ttu-id="27e80-112">Se l'utente concede l'autorizzazione, l'applicazione riceverà un input con sguardo.</span><span class="sxs-lookup"><span data-stu-id="27e80-112">If the user gives their permission, the application will get eye gaze input.</span></span> 

<span data-ttu-id="27e80-113">L'API di rilevamento degli occhi di Unreal è documentata [qui](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html)</span><span class="sxs-lookup"><span data-stu-id="27e80-113">Unreal’s eye tracking API is documented is [here](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html)</span></span>

<span data-ttu-id="27e80-114">I dettagli tecnici della verifica degli occhi sono disponibili [qui](eye-tracking.md)</span><span class="sxs-lookup"><span data-stu-id="27e80-114">The technical details of eye tracking are [here](eye-tracking.md)</span></span>

<span data-ttu-id="27e80-115">Si noti che, in particolare, per il rilevamento degli occhi di HoloLens è presente un singolo raggio di sguardi per entrambi gli occhi.</span><span class="sxs-lookup"><span data-stu-id="27e80-115">Note that specifically for Unreal, HoloLens eye tracking has a single gaze ray for both eyes.</span></span> <span data-ttu-id="27e80-116">HoloLens non offre la traccia stereoscopica degli occhi.</span><span class="sxs-lookup"><span data-stu-id="27e80-116">HoloLens doesn’t provide stereoscopic eye tracking.</span></span>

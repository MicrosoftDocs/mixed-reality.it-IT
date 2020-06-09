---
title: Input di sguardi in Unreal
description: Esercitazione sulla configurazione dell'input di sguardi per HoloLens e Unreal Engine
author: hferrone
ms.author: v-haferr
ms.date: 04/08/2020
ms.topic: article
keywords: Realtà mista di Windows, ologrammi, HoloLens 2, rilevamento degli occhi, input dello sguardo, visualizzazione montata a capo, Unreal Engine
ms.openlocfilehash: 0bc8b83a2e840b066eb5e30665584e1c68f7b021
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2020
ms.locfileid: "84551807"
---
# <a name="gaze-input"></a><span data-ttu-id="6840b-104">Input sguardo</span><span class="sxs-lookup"><span data-stu-id="6840b-104">Gaze Input</span></span>

## <a name="overview"></a><span data-ttu-id="6840b-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="6840b-105">Overview</span></span>

<span data-ttu-id="6840b-106">Il [plug-in realtà mista di Windows](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) non fornisce funzioni predefinite per l'input di sguardi, ma HoloLens 2 supporta la verifica degli occhi.</span><span class="sxs-lookup"><span data-stu-id="6840b-106">The [Windows Mixed Reality plugin](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) doesn’t provide any built-in functions for gaze input, but HoloLens 2 does support eye tracking.</span></span> <span data-ttu-id="6840b-107">Le funzionalità di rilevamento effettive vengono fornite dalle API di visualizzazione e **rilevamento degli occhi** **montate** da Unreal e includono:</span><span class="sxs-lookup"><span data-stu-id="6840b-107">The actual tracking features are provided by Unreal's **Head Mounted Display** and **Eye Tracking** APIs and include:</span></span>

- <span data-ttu-id="6840b-108">Informazioni sul dispositivo</span><span class="sxs-lookup"><span data-stu-id="6840b-108">Device information</span></span>
- <span data-ttu-id="6840b-109">Sensori di rilevamento</span><span class="sxs-lookup"><span data-stu-id="6840b-109">Tracking sensors</span></span>
- <span data-ttu-id="6840b-110">Orientamento e posizione</span><span class="sxs-lookup"><span data-stu-id="6840b-110">Orientation and position</span></span>
- <span data-ttu-id="6840b-111">Riquadri di ritaglio</span><span class="sxs-lookup"><span data-stu-id="6840b-111">Clipping panes</span></span>
- <span data-ttu-id="6840b-112">Informazioni sugli sguardi e sui dati di rilevamento</span><span class="sxs-lookup"><span data-stu-id="6840b-112">Gaze data and tracking information</span></span>

<span data-ttu-id="6840b-113">È possibile trovare l'elenco completo delle funzionalità disponibili nella documentazione di [visualizzazione](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) e [rilevamento degli occhi](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) di Unreal.</span><span class="sxs-lookup"><span data-stu-id="6840b-113">You can find the full list of features in Unreal's [Head Mounted Display](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) and [Eye Tracking](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) documentation.</span></span>

<span data-ttu-id="6840b-114">Oltre alle API Unreal, consultare la documentazione relativa all' [interazione basata sull'occhio](eye-gaze-interaction.md) per HoloLens 2 e leggere le informazioni sul funzionamento del [monitoraggio degli occhi in HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) .</span><span class="sxs-lookup"><span data-stu-id="6840b-114">In addition to the Unreal APIs, check out the documentation on [eye-gaze-based interaction](eye-gaze-interaction.md) for HoloLens 2 and read up on how [eye tracking on HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) works.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6840b-115">Il rilevamento degli occhi è supportato solo in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6840b-115">Eye tracking is only supported on HoloLens 2.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="6840b-116">Abilitazione del rilevamento degli occhi</span><span class="sxs-lookup"><span data-stu-id="6840b-116">Enabling eye tracking</span></span>
<span data-ttu-id="6840b-117">È necessario abilitare l'input dello sguardo nelle impostazioni del progetto HoloLens prima di poter usare le API non reali.</span><span class="sxs-lookup"><span data-stu-id="6840b-117">Gaze input needs to be enabled in the HoloLens project settings before you can use any of Unreal's APIs.</span></span> <span data-ttu-id="6840b-118">All'avvio dell'applicazione verrà visualizzata una richiesta di consenso visualizzata nella schermata seguente.</span><span class="sxs-lookup"><span data-stu-id="6840b-118">When the application starts you'll see a consent prompt shown in the screenshot below.</span></span>

- <span data-ttu-id="6840b-119">Selezionare **Sì** per impostare l'autorizzazione e ottenere l'accesso a sguardi input.</span><span class="sxs-lookup"><span data-stu-id="6840b-119">Select **Yes** to set the permission and get access to gaze input.</span></span> <span data-ttu-id="6840b-120">Se è necessario modificare questa impostazione in qualsiasi momento, è possibile trovarla nell'app **Impostazioni** .</span><span class="sxs-lookup"><span data-stu-id="6840b-120">If you need to change this setting at any time, it can be found in the **Settings** app.</span></span>

![Autorizzazioni di input per gli occhi](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> <span data-ttu-id="6840b-122">HoloLens Eye Tracking in Unreal ha solo un singolo raggio di sguardi per entrambi gli occhi anziché i due raggi necessari per il rilevamento stereoscopico, che non è supportato.</span><span class="sxs-lookup"><span data-stu-id="6840b-122">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

<span data-ttu-id="6840b-123">Questa è tutta la configurazione necessaria per iniziare ad aggiungere l'input dello sguardo alle app HoloLens 2 in modo irreale.</span><span class="sxs-lookup"><span data-stu-id="6840b-123">That's all the setup you'll need to start adding gaze input to your HoloLens 2 apps in Unreal.</span></span> <span data-ttu-id="6840b-124">Altre informazioni sull'input di sguardi e sul modo in cui influiscono sugli utenti in realtà mista sono disponibili nei collegamenti seguenti.</span><span class="sxs-lookup"><span data-stu-id="6840b-124">More information on gaze input and how it affects users in mixed reality can be found at the links below.</span></span> <span data-ttu-id="6840b-125">Quando si compilano esperienze interattive, tenere presente quanto prima.</span><span class="sxs-lookup"><span data-stu-id="6840b-125">Be sure to think about these when building your interactive experiences.</span></span>

## <a name="see-also"></a><span data-ttu-id="6840b-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6840b-126">See also</span></span>
* [<span data-ttu-id="6840b-127">Calibrazione</span><span class="sxs-lookup"><span data-stu-id="6840b-127">Calibration</span></span>](calibration.md)
* [<span data-ttu-id="6840b-128">Comodità</span><span class="sxs-lookup"><span data-stu-id="6840b-128">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="6840b-129">Sguardo e commit</span><span class="sxs-lookup"><span data-stu-id="6840b-129">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="6840b-130">Input vocale</span><span class="sxs-lookup"><span data-stu-id="6840b-130">Voice input</span></span>](voice-design.md)

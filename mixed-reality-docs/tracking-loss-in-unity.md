---
title: Perdita di rilevamento in Unity
description: Gestione di rilevamento delle perdite all'interno di un'app Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, rilevamento di perdite, rilevamento immagine perdita
ms.openlocfilehash: eb675860d67e9cad0d1129b3a6f61343990a4179
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602772"
---
# <a name="tracking-loss-in-unity"></a><span data-ttu-id="b8aa8-104">Perdita di rilevamento in Unity</span><span class="sxs-lookup"><span data-stu-id="b8aa8-104">Tracking loss in Unity</span></span>

<span data-ttu-id="b8aa8-105">Quando il dispositivo non è possibile individuare se stessa nel mondo, l'app si verifichi "perdita di rilevamento".</span><span class="sxs-lookup"><span data-stu-id="b8aa8-105">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="b8aa8-106">Per impostazione predefinita, Unity sarà sospendere il ciclo di aggiornamento e visualizzare un'immagine iniziale per l'utente.</span><span class="sxs-lookup"><span data-stu-id="b8aa8-106">By default, Unity will pause the update loop and display a splash image to the user.</span></span> <span data-ttu-id="b8aa8-107">Quando il rilevamento viene recuperato, l'immagine iniziale scompare e rimane il ciclo di aggiornamento continua.</span><span class="sxs-lookup"><span data-stu-id="b8aa8-107">When tracking is regained, the splash image goes away and the update loop continues.</span></span>

<span data-ttu-id="b8aa8-108">In alternativa, l'utente può gestire manualmente questa transizione annullando la partecipazione dell'impostazione.</span><span class="sxs-lookup"><span data-stu-id="b8aa8-108">As an alternative, the user can manually handle this transition by opting out of the setting.</span></span> <span data-ttu-id="b8aa8-109">Tutto il contenuto potrebbe sembrare diventi corpo bloccato durante la perdita di rilevamento se non viene eseguita alcuna operazione per gestirlo.</span><span class="sxs-lookup"><span data-stu-id="b8aa8-109">All content will seem to become body locked during tracking loss if nothing is done to handle it.</span></span>

## <a name="default-handling"></a><span data-ttu-id="b8aa8-110">La gestione predefinita.</span><span class="sxs-lookup"><span data-stu-id="b8aa8-110">Default Handling</span></span>

<span data-ttu-id="b8aa8-111">Per impostazione predefinita, il ciclo di aggiornamento dell'app, nonché tutti i messaggi e gli eventi arresterà per la durata della perdita di rilevamento.</span><span class="sxs-lookup"><span data-stu-id="b8aa8-111">By default, the update loop of the app as well as all messages and events will stop for the duration of tracking loss.</span></span> <span data-ttu-id="b8aa8-112">In quel momento stesso, verrà visualizzata all'utente un'immagine.</span><span class="sxs-lookup"><span data-stu-id="b8aa8-112">At that same time, an image will be displayed to the user.</span></span> <span data-ttu-id="b8aa8-113">È possibile personalizzare questa immagine andando su Modifica -> Impostazioni -> Windows Media Player, facendo clic immagine iniziale e l'impostazione dell'immagine di tenere traccia della perdita Holographic.</span><span class="sxs-lookup"><span data-stu-id="b8aa8-113">You can customize this image by going to Edit->Settings->Player, clicking Splash Image, and setting the Holographic Tracking Loss image.</span></span>

## <a name="manual-handling"></a><span data-ttu-id="b8aa8-114">Gestione manuale</span><span class="sxs-lookup"><span data-stu-id="b8aa8-114">Manual Handling</span></span>

<span data-ttu-id="b8aa8-115">Per gestire manualmente la perdita di rilevamento, è necessario passare a **Edit** > **impostazioni del progetto** > **Player**  >   **Scheda Impostazioni di piattaforma Windows Universal** > **immagine iniziale** > **Windows Holographic** e deselezionare l'opzione "nel rilevamento perdite pausa e Mostra immagine ".</span><span class="sxs-lookup"><span data-stu-id="b8aa8-115">To manually handle tracking loss, you need to go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform settings tab** > **Splash Image** > **Windows Holographic** and uncheck "On Tracking Loss Pause and Show Image".</span></span> <span data-ttu-id="b8aa8-116">Dopo questa operazione, è necessario gestire rilevamento delle modifiche con le API specificate di seguito.</span><span class="sxs-lookup"><span data-stu-id="b8aa8-116">After which, you need to handle tracking changes with the APIs specified below.</span></span>

<span data-ttu-id="b8aa8-117">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="b8aa8-117">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="b8aa8-118">**Tipo:** *WorldManager*</span><span class="sxs-lookup"><span data-stu-id="b8aa8-118">**Type:** *WorldManager*</span></span>

* <span data-ttu-id="b8aa8-119">World Manager espone un evento per il rilevamento di rilevamento persi/acquisita (*WorldManager.OnPositionalLocatorStateChanged*) e una proprietà per eseguire una query lo stato corrente (*WorldManager.state*)</span><span class="sxs-lookup"><span data-stu-id="b8aa8-119">World Manager exposes an event to detect tracking lost/gained (*WorldManager.OnPositionalLocatorStateChanged*) and a property to query the current state (*WorldManager.state*)</span></span>
* <span data-ttu-id="b8aa8-120">Quando lo stato di rilevamento non è attivo, la fotocamera non compariranno da convertire nel mondo virtuale anche quando l'utente viene convertito.</span><span class="sxs-lookup"><span data-stu-id="b8aa8-120">When the tracking state is not active, the camera will not appear to translate in the virtual world even as the user translates.</span></span> <span data-ttu-id="b8aa8-121">Di conseguenza gli oggetti non sono più corrisponderà a qualsiasi posizione fisica e tutti verranno visualizzati corpo bloccato.</span><span class="sxs-lookup"><span data-stu-id="b8aa8-121">This means objects will no longer correspond to any physical location and all will appear body locked.</span></span>

<span data-ttu-id="b8aa8-122">Quando si gestisce la registrazione delle modifiche nel proprio è necessario eseguire il polling per la proprietà state ogni frame o un handle di *OnPositionalLocatorStateChanged* evento.</span><span class="sxs-lookup"><span data-stu-id="b8aa8-122">When handling tracking changes on your own you either need to poll for the state property each frame or handle the *OnPositionalLocatorStateChanged* event.</span></span>

### <a name="polling"></a><span data-ttu-id="b8aa8-123">Polling</span><span class="sxs-lookup"><span data-stu-id="b8aa8-123">Polling</span></span>

<span data-ttu-id="b8aa8-124">Lo stato più importante è *PositionalLocatorState.Active* che indica che il rilevamento è completamente funzionale.</span><span class="sxs-lookup"><span data-stu-id="b8aa8-124">The most important state is *PositionalLocatorState.Active* which means tracking is fully functional.</span></span> <span data-ttu-id="b8aa8-125">Qualsiasi altro stato comporterà solo i delta rotazionali alla fotocamera principale.</span><span class="sxs-lookup"><span data-stu-id="b8aa8-125">Any other state will result in only rotational deltas to the main camera.</span></span> <span data-ttu-id="b8aa8-126">Ad esempio: </span><span class="sxs-lookup"><span data-stu-id="b8aa8-126">For example:</span></span>

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a><span data-ttu-id="b8aa8-127">Gestisce l'evento OnPositionalLocatorStateChanged</span><span class="sxs-lookup"><span data-stu-id="b8aa8-127">Handling the OnPositionalLocatorStateChanged event</span></span>

<span data-ttu-id="b8aa8-128">In alternativa e più semplice, è inoltre possibile sottoscrivere *OnPositionalLocatorStateChanged* per gestire le transizioni di:</span><span class="sxs-lookup"><span data-stu-id="b8aa8-128">Alternatively and more conveniently, you can also subscribe to *OnPositionalLocatorStateChanged* to handle the transitions:</span></span>

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a><span data-ttu-id="b8aa8-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b8aa8-129">See also</span></span>
* [<span data-ttu-id="b8aa8-130">Gestione di rilevamento delle perdite di DirectX</span><span class="sxs-lookup"><span data-stu-id="b8aa8-130">Handling tracking loss in DirectX</span></span>](coordinate-systems-in-directx.md#handling-tracking-loss)

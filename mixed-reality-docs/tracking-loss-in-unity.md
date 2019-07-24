---
title: Rilevamento della perdita in Unity
description: Gestione della perdita di rilevamento all'interno di un'app Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, perdita di rilevamento, immagine della perdita di rilevamento
ms.openlocfilehash: eb675860d67e9cad0d1129b3a6f61343990a4179
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548751"
---
# <a name="tracking-loss-in-unity"></a><span data-ttu-id="deeab-104">Rilevamento della perdita in Unity</span><span class="sxs-lookup"><span data-stu-id="deeab-104">Tracking loss in Unity</span></span>

<span data-ttu-id="deeab-105">Quando il dispositivo non è in grado di trovarsi nel mondo, l'app riscontra una "perdita di rilevamento".</span><span class="sxs-lookup"><span data-stu-id="deeab-105">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="deeab-106">Per impostazione predefinita, Unity sospende il ciclo di aggiornamento e visualizza un'immagine iniziale per l'utente.</span><span class="sxs-lookup"><span data-stu-id="deeab-106">By default, Unity will pause the update loop and display a splash image to the user.</span></span> <span data-ttu-id="deeab-107">Quando il rilevamento viene recuperato, l'immagine iniziale viene interrotta e il ciclo di aggiornamento continua.</span><span class="sxs-lookup"><span data-stu-id="deeab-107">When tracking is regained, the splash image goes away and the update loop continues.</span></span>

<span data-ttu-id="deeab-108">In alternativa, l'utente può gestire manualmente questa transizione scegliendo l'impostazione.</span><span class="sxs-lookup"><span data-stu-id="deeab-108">As an alternative, the user can manually handle this transition by opting out of the setting.</span></span> <span data-ttu-id="deeab-109">Se non viene eseguita alcuna operazione per la gestione, tutto il contenuto sembrerà bloccato nel corpo durante la perdita del rilevamento.</span><span class="sxs-lookup"><span data-stu-id="deeab-109">All content will seem to become body locked during tracking loss if nothing is done to handle it.</span></span>

## <a name="default-handling"></a><span data-ttu-id="deeab-110">Gestione predefinita</span><span class="sxs-lookup"><span data-stu-id="deeab-110">Default Handling</span></span>

<span data-ttu-id="deeab-111">Per impostazione predefinita, il ciclo di aggiornamento dell'app, nonché tutti i messaggi e gli eventi, si arresteranno per la durata della perdita del rilevamento.</span><span class="sxs-lookup"><span data-stu-id="deeab-111">By default, the update loop of the app as well as all messages and events will stop for the duration of tracking loss.</span></span> <span data-ttu-id="deeab-112">Allo stesso tempo, all'utente verrà visualizzata un'immagine.</span><span class="sxs-lookup"><span data-stu-id="deeab-112">At that same time, an image will be displayed to the user.</span></span> <span data-ttu-id="deeab-113">È possibile personalizzare questa immagine scegliendo Modifica-> Impostazioni-> Player, facendo clic su immagine iniziale e impostando l'immagine della perdita del rilevamento olografico.</span><span class="sxs-lookup"><span data-stu-id="deeab-113">You can customize this image by going to Edit->Settings->Player, clicking Splash Image, and setting the Holographic Tracking Loss image.</span></span>

## <a name="manual-handling"></a><span data-ttu-id="deeab-114">Gestione manuale</span><span class="sxs-lookup"><span data-stu-id="deeab-114">Manual Handling</span></span>

<span data-ttu-id="deeab-115">Per gestire manualmente la perdita del rilevamento, è necessario passare **a modifica** > **Impostazioni** > progetto**lettore** > piattaforma UWP (Universal Windows Platform)**immagine**  > inizialedellaschedaImpostazioni >  **Windows olografico** e deselezionare "on Tracking Loss pause and Show image".</span><span class="sxs-lookup"><span data-stu-id="deeab-115">To manually handle tracking loss, you need to go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform settings tab** > **Splash Image** > **Windows Holographic** and uncheck "On Tracking Loss Pause and Show Image".</span></span> <span data-ttu-id="deeab-116">Successivamente, è necessario gestire le modifiche di rilevamento con le API specificate di seguito.</span><span class="sxs-lookup"><span data-stu-id="deeab-116">After which, you need to handle tracking changes with the APIs specified below.</span></span>

<span data-ttu-id="deeab-117">**Namespace** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="deeab-117">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="deeab-118">**Tipo** *WorldManager*</span><span class="sxs-lookup"><span data-stu-id="deeab-118">**Type:** *WorldManager*</span></span>

* <span data-ttu-id="deeab-119">World Manager espone un evento per rilevare il rilevamento perso/acquisito (*WorldManager. OnPositionalLocatorStateChanged*) e una proprietà per eseguire una query sullo stato corrente (*WorldManager. state*)</span><span class="sxs-lookup"><span data-stu-id="deeab-119">World Manager exposes an event to detect tracking lost/gained (*WorldManager.OnPositionalLocatorStateChanged*) and a property to query the current state (*WorldManager.state*)</span></span>
* <span data-ttu-id="deeab-120">Quando lo stato di rilevamento non è attivo, la fotocamera non sembra tradursi nel mondo virtuale, anche quando l'utente si traduce.</span><span class="sxs-lookup"><span data-stu-id="deeab-120">When the tracking state is not active, the camera will not appear to translate in the virtual world even as the user translates.</span></span> <span data-ttu-id="deeab-121">Ciò significa che gli oggetti non corrisponderanno più a una posizione fisica e tutti verranno visualizzati corpo bloccati.</span><span class="sxs-lookup"><span data-stu-id="deeab-121">This means objects will no longer correspond to any physical location and all will appear body locked.</span></span>

<span data-ttu-id="deeab-122">Quando si gestiscono le modifiche di rilevamento, è necessario eseguire il polling per la proprietà di stato ogni frame o gestire l'evento *OnPositionalLocatorStateChanged* .</span><span class="sxs-lookup"><span data-stu-id="deeab-122">When handling tracking changes on your own you either need to poll for the state property each frame or handle the *OnPositionalLocatorStateChanged* event.</span></span>

### <a name="polling"></a><span data-ttu-id="deeab-123">Polling</span><span class="sxs-lookup"><span data-stu-id="deeab-123">Polling</span></span>

<span data-ttu-id="deeab-124">Lo stato più importante è *PositionalLocatorState. Active* , che significa che il rilevamento è completamente funzionante.</span><span class="sxs-lookup"><span data-stu-id="deeab-124">The most important state is *PositionalLocatorState.Active* which means tracking is fully functional.</span></span> <span data-ttu-id="deeab-125">Qualsiasi altro stato comporterà solo Delta rotazionali alla fotocamera principale.</span><span class="sxs-lookup"><span data-stu-id="deeab-125">Any other state will result in only rotational deltas to the main camera.</span></span> <span data-ttu-id="deeab-126">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="deeab-126">For example:</span></span>

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

### <a name="handling-the-onpositionallocatorstatechanged-event"></a><span data-ttu-id="deeab-127">Gestione dell'evento OnPositionalLocatorStateChanged</span><span class="sxs-lookup"><span data-stu-id="deeab-127">Handling the OnPositionalLocatorStateChanged event</span></span>

<span data-ttu-id="deeab-128">In alternativa, è anche possibile eseguire la sottoscrizione a *OnPositionalLocatorStateChanged* per gestire le transizioni:</span><span class="sxs-lookup"><span data-stu-id="deeab-128">Alternatively and more conveniently, you can also subscribe to *OnPositionalLocatorStateChanged* to handle the transitions:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="deeab-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="deeab-129">See also</span></span>
* [<span data-ttu-id="deeab-130">Gestione della perdita di rilevamento in DirectX</span><span class="sxs-lookup"><span data-stu-id="deeab-130">Handling tracking loss in DirectX</span></span>](coordinate-systems-in-directx.md#handling-tracking-loss)

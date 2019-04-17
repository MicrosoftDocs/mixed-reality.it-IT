---
title: Punto di stato attivo in Unity
description: La modifica manuale di stabilità ologrammi in Unity, impostare il punto di stato attivo
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, il punto di stato attivo, piano messa a fuoco, piano di stabilizzazione, punto di stabilizzazione, reprojection, LSR, buffer di profondità
ms.openlocfilehash: 0f43c37df66ecada86dcb309fcd58d822f0f3481
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604880"
---
# <a name="focus-point-in-unity"></a><span data-ttu-id="1a0e0-104">Punto di stato attivo in Unity</span><span class="sxs-lookup"><span data-stu-id="1a0e0-104">Focus point in Unity</span></span>

<span data-ttu-id="1a0e0-105">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="1a0e0-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="1a0e0-106">**Tipo**: *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="1a0e0-106">**Type**: *HolographicSettings*</span></span>

<span data-ttu-id="1a0e0-107">Il [concentrarsi punto](hologram-stability.md#stabilization-plane) insieme per fornire un suggerimento su come eseguire meglio la stabilizzazione nel vntana attualmente HoloLens in corso visualizzabile.</span><span class="sxs-lookup"><span data-stu-id="1a0e0-107">The [focus point](hologram-stability.md#stabilization-plane) can be set to provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed.</span></span>

<span data-ttu-id="1a0e0-108">Se si desidera impostare il punto di stato attivo in Unity, è necessario impostare ogni tramite cornice *HolographicSettings.SetFocusPointForFrame()*.</span><span class="sxs-lookup"><span data-stu-id="1a0e0-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()*.</span></span> <span data-ttu-id="1a0e0-109">Se il punto di attivazione non è impostato per un frame, verrà utilizzato il piano di stabilizzazione di default.</span><span class="sxs-lookup"><span data-stu-id="1a0e0-109">If the Focus Point is not set for a frame, the default stabilization plane will be used.</span></span>

> [!NOTE]
> <span data-ttu-id="1a0e0-110">Per impostazione predefinita, i nuovi progetti di Unity impostare l'opzione "Abilita condivisione Buffer profondità".</span><span class="sxs-lookup"><span data-stu-id="1a0e0-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="1a0e0-111">Con questa opzione, un'app Unity in esecuzione su un auricolare desktop coinvolgente e concreto o un HoloLens che eseguono Windows 10 April 2018 Update (RS4) o in un secondo momento nel buffer di profondità di Windows per ottimizzare la stabilità di ologramma automaticamente, senza specificare l'app invia una punto di attivazione:</span><span class="sxs-lookup"><span data-stu-id="1a0e0-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="1a0e0-112">In un auricolare desktop coinvolgenti, ciò consentirà reprojection basato su profondità per pixel.</span><span class="sxs-lookup"><span data-stu-id="1a0e0-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="1a0e0-113">In un HoloLens che eseguono Windows 10 April 2018 Update o versione successiva, questo analizzerà il buffer di profondità per scegliere un piano ottimale stabilizzazione automaticamente.</span><span class="sxs-lookup"><span data-stu-id="1a0e0-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="1a0e0-114">Entrambi gli approcci devono fornire anche una migliore qualità dell'immagine senza lavoro esplicito dall'app per selezionare un punto di stato attivo ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="1a0e0-114">Either approach should provide even better image quality without explicit work by your app to select a focus point each frame.</span></span>  <span data-ttu-id="1a0e0-115">Si noti che se si fornisce manualmente un punto di stato attivo, che sostituirà il comportamento automatico descritto in precedenza e in genere ridurrà la stabilità di ologramma.</span><span class="sxs-lookup"><span data-stu-id="1a0e0-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="1a0e0-116">In generale, è necessario specificare solo un punto di attivazione manuale quando l'app è in esecuzione su un HoloLens che non è ancora stato aggiornato a Windows 10 April 2018 Update.</span><span class="sxs-lookup"><span data-stu-id="1a0e0-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="1a0e0-117">Esempio</span><span class="sxs-lookup"><span data-stu-id="1a0e0-117">Example</span></span>

<span data-ttu-id="1a0e0-118">Esistono diversi modi per impostare il punto di stato attivo, come suggerito dall'overload disponibile nel *SetFocusPointForFrame* funzione statica.</span><span class="sxs-lookup"><span data-stu-id="1a0e0-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="1a0e0-119">Riportati di seguito è riportato un esempio semplice per impostare il piano dello stato attivo per l'oggetto fornito ogni frame:</span><span class="sxs-lookup"><span data-stu-id="1a0e0-119">Presented below is a simple example to set the focus plane to the provided object each frame:</span></span>

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's 
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to 
    // the normal of the plane and ensure the user does not pass through the 
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

<span data-ttu-id="1a0e0-120">Si noti che il semplice codice sopra riportato potrebbe finire la riduzione di stabilità ologrammi se l'oggetto con lo stato attivo finisce dietro l'utente.</span><span class="sxs-lookup"><span data-stu-id="1a0e0-120">Note that the simple code above may end up reducing hologram stability if the focused object ends up behind the user.</span></span>  <span data-ttu-id="1a0e0-121">Ecco perché è in genere consigliabile impostare "Consenti condivisione Buffer profondità" anziché specificare manualmente un punto di stato attivo.</span><span class="sxs-lookup"><span data-stu-id="1a0e0-121">This is why you should generally set "Enable Depth Buffer Sharing" instead of manually specifying a focus point.</span></span>

### <a name="see-also"></a><span data-ttu-id="1a0e0-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1a0e0-122">See also</span></span>
* [<span data-ttu-id="1a0e0-123">Piano di stabilizzazione</span><span class="sxs-lookup"><span data-stu-id="1a0e0-123">Stabilization plane</span></span>](hologram-stability.md#stabilization-plane)

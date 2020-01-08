---
title: Punto di messa a fuoco in Unity
description: Ottimizzazione manuale della stabilità degli ologrammi in Unity impostando il punto di attivazione
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, punto focale, piano di messa a fuoco, piano di stabilizzazione, punto di stabilizzazione, riproiezione, LSR, buffer di profondità
ms.openlocfilehash: 9a7f30b552242b24a9a7b260b6574690a27d2c1d
ms.sourcegitcommit: 7e8b9de561cbc8483e84511f3e9cbd779f3a999f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/27/2019
ms.locfileid: "75502622"
---
# <a name="focus-point-in-unity"></a><span data-ttu-id="d7a46-104">Punto di messa a fuoco in Unity</span><span class="sxs-lookup"><span data-stu-id="d7a46-104">Focus point in Unity</span></span>

<span data-ttu-id="d7a46-105">**Spazio dei nomi:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="d7a46-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="d7a46-106">**Tipo**: *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="d7a46-106">**Type**: *HolographicSettings*</span></span>

<span data-ttu-id="d7a46-107">Il [punto di interesse](hologram-stability.md#reprojection) può essere impostato in modo da fornire a HoloLens un suggerimento su come eseguire al meglio la stabilizzazione sugli ologrammi attualmente in fase di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="d7a46-107">The [focus point](hologram-stability.md#reprojection) can be set to provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed.</span></span>

<span data-ttu-id="d7a46-108">Se si vuole impostare il punto di messa a fuoco in Unity, è necessario impostare ogni fotogramma usando *HolographicSettings. SetFocusPointForFrame ()* .</span><span class="sxs-lookup"><span data-stu-id="d7a46-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()*.</span></span> <span data-ttu-id="d7a46-109">Se il punto di attivazione non è impostato per un frame, verrà utilizzato il piano di stabilizzazione predefinito.</span><span class="sxs-lookup"><span data-stu-id="d7a46-109">If the Focus Point is not set for a frame, the default stabilization plane will be used.</span></span>

> [!NOTE]
> <span data-ttu-id="d7a46-110">Per impostazione predefinita, i nuovi progetti Unity hanno l'opzione "Abilita condivisione buffer di profondità" impostata.</span><span class="sxs-lookup"><span data-stu-id="d7a46-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="d7a46-111">Con questa opzione, un'app Unity in esecuzione in una cuffia desktop immersiva o un HoloLens che esegue l'aggiornamento di Windows 10 aprile 2018 (RS4) o versione successiva invierà il buffer di profondità a Windows per ottimizzare automaticamente la stabilità dell'ologramma, senza che l'app specifichi punto di interesse:</span><span class="sxs-lookup"><span data-stu-id="d7a46-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="d7a46-112">In un auricolare desktop immersivo, verrà abilitata la riproiezione basata sulla profondità per pixel.</span><span class="sxs-lookup"><span data-stu-id="d7a46-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="d7a46-113">In una HoloLens che esegue l'aggiornamento di Windows 10 aprile 2018 o versione successiva, verrà analizzato il buffer di profondità per selezionare automaticamente un piano di stabilizzazione ottimale.</span><span class="sxs-lookup"><span data-stu-id="d7a46-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="d7a46-114">Entrambi gli approcci dovrebbero fornire una qualità dell'immagine ancora migliore senza lavoro esplicito da parte dell'app per selezionare un punto di interesse per ogni frame.</span><span class="sxs-lookup"><span data-stu-id="d7a46-114">Either approach should provide even better image quality without explicit work by your app to select a focus point for each frame.</span></span>  <span data-ttu-id="d7a46-115">Si noti che se si specifica un punto di interesse manualmente, che sostituisce il comportamento automatico descritto in precedenza, e in genere ridurrà la stabilità degli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="d7a46-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="d7a46-116">In genere, è necessario specificare un punto di messa a fuoco manuale solo quando l'app è in esecuzione in un HoloLens che non è ancora stato aggiornato all'aggiornamento di Windows 10 aprile 2018.</span><span class="sxs-lookup"><span data-stu-id="d7a46-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="d7a46-117">Esempio</span><span class="sxs-lookup"><span data-stu-id="d7a46-117">Example</span></span>

<span data-ttu-id="d7a46-118">Esistono diversi modi per impostare il punto di interesse, come suggerito dagli overload disponibili nella funzione statica *SetFocusPointForFrame* .</span><span class="sxs-lookup"><span data-stu-id="d7a46-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="d7a46-119">Di seguito è riportato un semplice esempio per impostare il piano di attivazione sull'oggetto fornito per ogni frame:</span><span class="sxs-lookup"><span data-stu-id="d7a46-119">Presented below is a simple example to set the focus plane to the provided object for each frame:</span></span>

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

<span data-ttu-id="d7a46-120">Si noti che il codice precedente può finire a ridurre la stabilità dell'ologramma se l'oggetto con stato attivo termina dietro l'utente.</span><span class="sxs-lookup"><span data-stu-id="d7a46-120">Note that the simple code above may end up reducing hologram stability if the focused object ends up behind the user.</span></span>  <span data-ttu-id="d7a46-121">Questo è il motivo per cui in genere è necessario impostare "Abilita condivisione buffer di profondità" anziché specificare manualmente un punto di interesse.</span><span class="sxs-lookup"><span data-stu-id="d7a46-121">This is why you should generally set "Enable Depth Buffer Sharing" instead of manually specifying a focus point.</span></span>

### <a name="see-also"></a><span data-ttu-id="d7a46-122">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="d7a46-122">See also</span></span>
* [<span data-ttu-id="d7a46-123">Piano di stabilizzazione</span><span class="sxs-lookup"><span data-stu-id="d7a46-123">Stabilization plane</span></span>](hologram-stability.md#reprojection)

---
title: Estasiati Unity
description: Sguardo è un modo primario per gli utenti come destinazione il vntana che consente di creare l'app nella realtà mista.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: estasiati, unity, ologrammi, realtà mista
ms.openlocfilehash: b2cc86db156a1e97b013e4cd6debe3abe5ffb6dd
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453716"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="cea58-104">Head estasiati Unity</span><span class="sxs-lookup"><span data-stu-id="cea58-104">Head gaze in Unity</span></span>

<span data-ttu-id="cea58-105">[Estasiati](gaze.md) è un modo per gli utenti come destinazione primario di [vntana](hologram.md) consente di creare l'app nel [realtà mista](mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="cea58-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="cea58-106">Implementazione sguardo head</span><span class="sxs-lookup"><span data-stu-id="cea58-106">Implementing head gaze</span></span>

<span data-ttu-id="cea58-107">Concettualmente [estasiati](gaze.md) viene implementato proiettando un raggio dall'inizio dell'utente in cui le cuffie, nella direzione avanti sono affiancate e determinare quali che ray è in conflitto con.</span><span class="sxs-lookup"><span data-stu-id="cea58-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="cea58-108">In Unity, posizione principale dell'utente e la direzione sono esposte tramite l'oggetto principale di Unity [fotocamera](camera-in-unity.md), in particolare [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="cea58-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="cea58-109">La chiamata [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) comporta un' [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) struttura che contiene informazioni relative la collisione tra cui il punto 3D in cui si è verificato conflitto e gli altri elementi GameObject raggio sguardo sono in contrasto con.</span><span class="sxs-lookup"><span data-stu-id="cea58-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="cea58-110">Esempio: Implementare sguardo head</span><span class="sxs-lookup"><span data-stu-id="cea58-110">Example: Implement head gaze</span></span>

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a><span data-ttu-id="cea58-111">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="cea58-111">Best Practices</span></span>

<span data-ttu-id="cea58-112">Mentre l'esempio precedente illustra come eseguire un singolo raycast in un ciclo di aggiornamento per trovare la destinazione sguardo, è consigliabile eseguire questa operazione in un singolo oggetto sguardo invece di eseguire questa operazione in qualsiasi oggetto che è potenzialmente interessato l'oggetto in corso gazed nella gestione.</span><span class="sxs-lookup"><span data-stu-id="cea58-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="cea58-113">In questo modo l'app Salva l'elaborazione in questo modo un solo sguardo raycast ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="cea58-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="cea58-114">Visualizzazione sguardo</span><span class="sxs-lookup"><span data-stu-id="cea58-114">Visualizing Gaze</span></span>

<span data-ttu-id="cea58-115">Esattamente come sul desktop in cui è usare il puntatore del mouse di destinazione e interagire con il contenuto, è necessario implementare una [cursore](cursors.md) che rappresenta sguardo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="cea58-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="cea58-116">In questo modo la fiducia degli utenti sugli aspetti che stanno per interagirvi.</span><span class="sxs-lookup"><span data-stu-id="cea58-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit-v2"></a><span data-ttu-id="cea58-117">Realtà mista estasiati Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="cea58-117">Gaze in Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="cea58-118">È possibile accedere a sguardo dal [Manager di input](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) MRTK v2.</span><span class="sxs-lookup"><span data-stu-id="cea58-118">You can access gaze from the [input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="cea58-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cea58-119">See also</span></span>
* [<span data-ttu-id="cea58-120">Fotocamera</span><span class="sxs-lookup"><span data-stu-id="cea58-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="cea58-121">Input sguardo</span><span class="sxs-lookup"><span data-stu-id="cea58-121">Gaze input</span></span>](gaze.md)
* [<span data-ttu-id="cea58-122">Cursori</span><span class="sxs-lookup"><span data-stu-id="cea58-122">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="cea58-123">Selezione della destinazione con lo sguardo</span><span class="sxs-lookup"><span data-stu-id="cea58-123">Gaze targeting</span></span>](gaze-targeting.md)

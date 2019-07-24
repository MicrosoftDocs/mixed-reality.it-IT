---
title: Sguardo in Unity
description: Lo sguardo è un modo principale per consentire agli utenti di individuare gli ologrammi creati dall'app in realtà mista.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: sguardo, Unity, ologramma, realtà mista
ms.openlocfilehash: b2cc86db156a1e97b013e4cd6debe3abe5ffb6dd
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453716"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="1c71d-104">Sguardo a testa in Unity</span><span class="sxs-lookup"><span data-stu-id="1c71d-104">Head gaze in Unity</span></span>

<span data-ttu-id="1c71d-105">Lo [sguardo](gaze.md) è un modo principale per consentire agli utenti di individuare gli [ologrammi](hologram.md) creati dall'app in [realtà mista](mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="1c71d-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="1c71d-106">Implementazione dello sguardo a capo</span><span class="sxs-lookup"><span data-stu-id="1c71d-106">Implementing head gaze</span></span>

<span data-ttu-id="1c71d-107">Dal punto di vista concettuale, lo [sguardo](gaze.md) viene implementato proiettando un raggio dalla parte principale dell'utente in cui si trova l'auricolare, nella direzione in avanti che si trovano e determinano la collisione tra i raggi.</span><span class="sxs-lookup"><span data-stu-id="1c71d-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="1c71d-108">In Unity, la posizione e la direzione della testa dell'utente vengono esposte tramite la [fotocamera](camera-in-unity.md)principale di Unity, in particolare [UnityEngine. camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. inoltr](http://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine. camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="1c71d-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="1c71d-109">La chiamata a [Physics. RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) genera una struttura [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) che contiene informazioni sulla collisione, tra cui il punto 3D in cui si è verificata la collisione e l'altro GameObject il raggio di sguardi in collisione con.</span><span class="sxs-lookup"><span data-stu-id="1c71d-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="1c71d-110">Esempio: Implementare lo sguardo a capo</span><span class="sxs-lookup"><span data-stu-id="1c71d-110">Example: Implement head gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="1c71d-111">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="1c71d-111">Best Practices</span></span>

<span data-ttu-id="1c71d-112">Mentre nell'esempio precedente viene illustrato come eseguire un singolo Raycast in un ciclo di aggiornamento per trovare la destinazione dello sguardo, è consigliabile eseguire questa operazione in un singolo oggetto che gestisce lo sguardo invece di eseguire questa operazione in un oggetto potenzialmente interessato all'oggetto che si sta osservando.</span><span class="sxs-lookup"><span data-stu-id="1c71d-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="1c71d-113">Ciò consente all'app di salvare l'elaborazione eseguendo un solo sguardo Raycast ogni frame.</span><span class="sxs-lookup"><span data-stu-id="1c71d-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="1c71d-114">Visualizzazione dello sguardo</span><span class="sxs-lookup"><span data-stu-id="1c71d-114">Visualizing Gaze</span></span>

<span data-ttu-id="1c71d-115">Proprio come nel desktop in cui si usa un puntatore del mouse per la destinazione e l'interazione con il contenuto, è necessario implementare un [cursore](cursors.md) che rappresenta lo sguardo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="1c71d-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="1c71d-116">In questo modo l'utente è in confidenza con l'interazione con.</span><span class="sxs-lookup"><span data-stu-id="1c71d-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit-v2"></a><span data-ttu-id="1c71d-117">Sguardo in Mixed Reality toolkit V2</span><span class="sxs-lookup"><span data-stu-id="1c71d-117">Gaze in Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="1c71d-118">È possibile accedere a sguardi da [Gestione input](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK V2.</span><span class="sxs-lookup"><span data-stu-id="1c71d-118">You can access gaze from the [input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c71d-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1c71d-119">See also</span></span>
* [<span data-ttu-id="1c71d-120">Fotocamera</span><span class="sxs-lookup"><span data-stu-id="1c71d-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="1c71d-121">Input sguardo</span><span class="sxs-lookup"><span data-stu-id="1c71d-121">Gaze input</span></span>](gaze.md)
* [<span data-ttu-id="1c71d-122">Cursori</span><span class="sxs-lookup"><span data-stu-id="1c71d-122">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="1c71d-123">Selezione della destinazione con lo sguardo</span><span class="sxs-lookup"><span data-stu-id="1c71d-123">Gaze targeting</span></span>](gaze-targeting.md)

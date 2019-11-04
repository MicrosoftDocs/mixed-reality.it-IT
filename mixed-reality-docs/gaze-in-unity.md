---
title: Sguardo in Unity
description: Lo sguardo è un modo principale per consentire agli utenti di individuare gli ologrammi creati dall'app in realtà mista.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: occhi, sguardi, Unity, ologramma, realtà mista
ms.openlocfilehash: 8222a5199cc1ea35429f21e7490e1eff49fcd1bc
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435300"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="15da8-104">Sguardo da capo in Unity</span><span class="sxs-lookup"><span data-stu-id="15da8-104">Head-gaze in Unity</span></span>

<span data-ttu-id="15da8-105">Lo [sguardo](gaze-and-commit.md) è un modo principale per consentire agli utenti di individuare gli [ologrammi](hologram.md) creati dall'app in [realtà mista](mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="15da8-105">[Gaze](gaze-and-commit.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="15da8-106">Implementazione dell'Head-sguardi</span><span class="sxs-lookup"><span data-stu-id="15da8-106">Implementing head-gaze</span></span>

<span data-ttu-id="15da8-107">Dal punto di vista concettuale, l' [Head-sguardi](gaze-and-commit.md) viene implementato proiettando un raggio dalla parte iniziale dell'utente in cui si trova l'auricolare, nella direzione in avanti che si trovano e determinano la collisione del raggio.</span><span class="sxs-lookup"><span data-stu-id="15da8-107">Conceptually, [head-gaze](gaze-and-commit.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="15da8-108">In Unity, la posizione e la direzione della testa dell'utente vengono esposte tramite la [fotocamera](camera-in-unity.md)principale di Unity, in particolare [UnityEngine. camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. inoltr](https://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine. camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="15da8-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="15da8-109">La chiamata a [Physics. RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) genera una struttura [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) che contiene informazioni sulla collisione, tra cui il punto 3D in cui si è verificata la collisione e l'altro GameObject del raggio di puntamento.</span><span class="sxs-lookup"><span data-stu-id="15da8-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the head-gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="15da8-110">Esempio: implementare l'Head-sguardi</span><span class="sxs-lookup"><span data-stu-id="15da8-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="15da8-111">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="15da8-111">Best practices</span></span>

<span data-ttu-id="15da8-112">Mentre l'esempio precedente illustra come eseguire un singolo Raycast in un ciclo di aggiornamento per trovare la destinazione in cui si trovano i puntini dell'utente, è consigliabile eseguire questa operazione in un singolo oggetto che gestisce il testing, invece di eseguire questa operazione in qualsiasi oggetto potenzialmente interessato al oggetto t guardato.</span><span class="sxs-lookup"><span data-stu-id="15da8-112">While the example above demonstrates how to do a single raycast in an update loop to find the target the user's head points at, it is recommended to do this in a single object managing head-gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="15da8-113">In questo modo, l'app consente di salvare l'elaborazione eseguendo solo uno sguardo a capo Raycast ogni frame.</span><span class="sxs-lookup"><span data-stu-id="15da8-113">This lets your app save processing by doing just one head-gaze raycast each frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="15da8-114">Visualizzazione dell'Head-sguardi</span><span class="sxs-lookup"><span data-stu-id="15da8-114">Visualizing head-gaze</span></span>

<span data-ttu-id="15da8-115">Proprio come nel desktop in cui si usa un puntatore del mouse per la destinazione e l'interazione con il contenuto, è necessario implementare un [cursore](cursors.md) che rappresenti il capo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="15da8-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="15da8-116">In questo modo l'utente è in confidenza con l'interazione con.</span><span class="sxs-lookup"><span data-stu-id="15da8-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a><span data-ttu-id="15da8-117">Head-sguardi nel Toolkit di realtà misto V2</span><span class="sxs-lookup"><span data-stu-id="15da8-117">Head-gaze in the Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="15da8-118">È possibile accedere a Head-sguardi da [Gestione input](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK V2.</span><span class="sxs-lookup"><span data-stu-id="15da8-118">You can access head-gaze from the [Input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="15da8-119">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="15da8-119">See also</span></span>
* [<span data-ttu-id="15da8-120">Fotocamera</span><span class="sxs-lookup"><span data-stu-id="15da8-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="15da8-121">Cursori</span><span class="sxs-lookup"><span data-stu-id="15da8-121">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="15da8-122">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="15da8-122">Head-gaze and commit</span></span>](gaze-and-commit.md)

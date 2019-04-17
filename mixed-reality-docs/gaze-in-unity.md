---
title: Estasiati Unity
description: Sguardo è un modo primario per gli utenti come destinazione il vntana che consente di creare l'app nella realtà mista.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: estasiati, unity, ologrammi, realtà mista
ms.openlocfilehash: 09915479a9eef95c5ce4533371e113ab6191a331
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604800"
---
# <a name="gaze-in-unity"></a><span data-ttu-id="5bfae-104">Estasiati Unity</span><span class="sxs-lookup"><span data-stu-id="5bfae-104">Gaze in Unity</span></span>

<span data-ttu-id="5bfae-105">[Estasiati](gaze.md) è un modo per gli utenti come destinazione primario di [vntana](hologram.md) consente di creare l'app nel [realtà mista](mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="5bfae-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [mixed reality](mixed-reality.md).</span></span>

## <a name="implementing-gaze"></a><span data-ttu-id="5bfae-106">Implementazione sguardo</span><span class="sxs-lookup"><span data-stu-id="5bfae-106">Implementing Gaze</span></span>

<span data-ttu-id="5bfae-107">Concettualmente [estasiati](gaze.md) viene implementato proiettando un raggio dall'inizio dell'utente in cui le cuffie, nella direzione avanti sono affiancate e determinare quali che ray è in conflitto con.</span><span class="sxs-lookup"><span data-stu-id="5bfae-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="5bfae-108">In Unity, posizione principale dell'utente e la direzione sono esposte tramite l'oggetto principale di Unity [fotocamera](camera-in-unity.md), in particolare [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="5bfae-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="5bfae-109">La chiamata [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) comporta un' [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) struttura che contiene informazioni relative la collisione tra cui il punto 3D in cui si è verificato conflitto e gli altri elementi GameObject raggio sguardo sono in contrasto con.</span><span class="sxs-lookup"><span data-stu-id="5bfae-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-gaze"></a><span data-ttu-id="5bfae-110">Esempio: Implementare sguardo</span><span class="sxs-lookup"><span data-stu-id="5bfae-110">Example: Implement Gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="5bfae-111">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="5bfae-111">Best Practices</span></span>

<span data-ttu-id="5bfae-112">Mentre l'esempio precedente illustra come eseguire un singolo raycast in un ciclo di aggiornamento per trovare la destinazione sguardo, è consigliabile eseguire questa operazione in un singolo oggetto sguardo invece di eseguire questa operazione in qualsiasi oggetto che è potenzialmente interessato l'oggetto in corso gazed nella gestione.</span><span class="sxs-lookup"><span data-stu-id="5bfae-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="5bfae-113">In questo modo l'app Salva l'elaborazione in questo modo un solo sguardo raycast ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="5bfae-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="5bfae-114">Visualizzazione sguardo</span><span class="sxs-lookup"><span data-stu-id="5bfae-114">Visualizing Gaze</span></span>

<span data-ttu-id="5bfae-115">Esattamente come sul desktop in cui è usare il puntatore del mouse di destinazione e interagire con il contenuto, è necessario implementare una [cursore](cursors.md) che rappresenta sguardo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="5bfae-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="5bfae-116">In questo modo la fiducia degli utenti sugli aspetti che stanno per interagirvi.</span><span class="sxs-lookup"><span data-stu-id="5bfae-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit"></a><span data-ttu-id="5bfae-117">Estasiati nel Toolkit di realtà mista</span><span class="sxs-lookup"><span data-stu-id="5bfae-117">Gaze in Mixed Reality Toolkit</span></span>
<span data-ttu-id="5bfae-118">Quando si importano [MRTK rilasciare pacchetti Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) o clonare il progetto dal [repository di GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity), si desidera trovare un nuovo menu 'Toolkit realtà mista' in Unity.</span><span class="sxs-lookup"><span data-stu-id="5bfae-118">When you import [MRTK release Unity packages](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) or clone the project from the [GitHub repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), you are going to find a new menu 'Mixed Reality Toolkit' in Unity.</span></span> <span data-ttu-id="5bfae-119">Nel menu 'Configura', verrà visualizzato il menu 'Applica misto realtà scena impostazioni'.</span><span class="sxs-lookup"><span data-stu-id="5bfae-119">Under 'Configure' menu, you will see the menu 'Apply Mixed Reality Scene Settings'.</span></span> <span data-ttu-id="5bfae-120">Quando si fa clic si, rimuove la fotocamera predefinita e aggiunge i componenti fondamentali - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), e [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span><span class="sxs-lookup"><span data-stu-id="5bfae-120">When you click it, it removes the default camera and adds foundational components - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), and [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span></span>

<span data-ttu-id="5bfae-121">![Menu MRTK per l'installazione di scena](images/MRTK_Input_Menu.png)</span><span class="sxs-lookup"><span data-stu-id="5bfae-121">![MRTK Menu for scene setup](images/MRTK_Input_Menu.png)</span></span><br>
<span data-ttu-id="5bfae-122">*Menu MRTK per l'installazione di scena*</span><span class="sxs-lookup"><span data-stu-id="5bfae-122">*MRTK Menu for scene setup*</span></span>

<span data-ttu-id="5bfae-123">![Programma di installazione automatica di scena in MRTK](images/MRTK_HowTo_Input1.png)</span><span class="sxs-lookup"><span data-stu-id="5bfae-123">![Automatic scene setup in MRTK](images/MRTK_HowTo_Input1.png)</span></span><br>
<span data-ttu-id="5bfae-124">*Programma di installazione automatica di scena in MRTK*</span><span class="sxs-lookup"><span data-stu-id="5bfae-124">*Automatic scene setup in MRTK*</span></span>

### <a name="gaze-related-scripts-in-mixed-reality-toolkit"></a><span data-ttu-id="5bfae-125">Estasiati script correlati nel Toolkit di realtà mista</span><span class="sxs-lookup"><span data-stu-id="5bfae-125">Gaze related scripts in Mixed Reality Toolkit</span></span>
<span data-ttu-id="5bfae-126">Toolkit di realtà mista include InputManager prefab [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs) e [estasiati stabilizzatore](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs).</span><span class="sxs-lookup"><span data-stu-id="5bfae-126">Mixed Reality Toolkit's InputManager prefab includes [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs) and [Gaze Stabilizer](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs).</span></span> <span data-ttu-id="5bfae-127">Sotto [SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs), è possibile assegnare il cursore personalizzato.</span><span class="sxs-lookup"><span data-stu-id="5bfae-127">Under [SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs), you can assign your custom Cursor.</span></span> <span data-ttu-id="5bfae-128">Parola chiave default, animata [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab) viene assegnato.</span><span class="sxs-lookup"><span data-stu-id="5bfae-128">In default, animated [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab) is assigned.</span></span>

<span data-ttu-id="5bfae-129">[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) e [CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) viene illustrato come visualizzare lo sguardo utilizzano i cursori.</span><span class="sxs-lookup"><span data-stu-id="5bfae-129">[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) and [CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) shows you how to visualize your Gaze using Cursors.</span></span>

## <a name="see-also"></a><span data-ttu-id="5bfae-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5bfae-130">See also</span></span>
* [<span data-ttu-id="5bfae-131">Fotocamera</span><span class="sxs-lookup"><span data-stu-id="5bfae-131">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="5bfae-132">Sguardo</span><span class="sxs-lookup"><span data-stu-id="5bfae-132">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="5bfae-133">Cursori</span><span class="sxs-lookup"><span data-stu-id="5bfae-133">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="5bfae-134">Sguardo targeting</span><span class="sxs-lookup"><span data-stu-id="5bfae-134">Gaze targeting</span></span>](gaze-targeting.md)

---
title: Sistemi di coordinate in Unity
description: Scopri come creare esperienze di realtà mista, in base a scalabilità e su scala globale in Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema di coordinate, sistema di coordinate spaziali, solo orientamento, scalabilità verticale, scalabilità, scalabilità, scalabilità, scala globale, 360 gradi, seduto, in piedi, stanza, mondo, scala, posizione, orientamento, Unity, ancoraggio, ancoraggio spaziale, ancoraggio globale, con blocco globale, blocco globale, con blocco del corpo, blocco del corpo, perdita di rilevamento, locatability, limiti, recenter
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375768"
---
# <a name="coordinate-systems-in-unity"></a><span data-ttu-id="ecc4e-104">Sistemi di coordinate in Unity</span><span class="sxs-lookup"><span data-stu-id="ecc4e-104">Coordinate systems in Unity</span></span>

<span data-ttu-id="ecc4e-105">La realtà mista di Windows supporta le app in un'ampia gamma di [scale di esperienza](coordinate-systems.md), da app di solo orientamento e scalabilità verticale fino ad app a scalabilità.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-105">Windows Mixed Reality supports apps across a wide range of [experience scales](coordinate-systems.md), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="ecc4e-106">In HoloLens è possibile proseguire e creare app su scala mondiale che consentono agli utenti di superare i 5 metri, esplorando un'intera superficie di un edificio e oltre.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-106">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="ecc4e-107">Il primo passaggio per creare un'esperienza di realtà mista in Unity consiste nel determinare quale [scalabilità dell'esperienza](coordinate-systems.md) sarà destinata all'app.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-107">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](coordinate-systems.md) your app will target.</span></span>

## <a name="building-an-orientation-only-or-seated-scale-experience"></a><span data-ttu-id="ecc4e-108">Creazione di un'esperienza di solo orientamento o con scalabilità verticale</span><span class="sxs-lookup"><span data-stu-id="ecc4e-108">Building an orientation-only or seated-scale experience</span></span>

<span data-ttu-id="ecc4e-109">**Spazio dei nomi:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="ecc4e-109">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="ecc4e-110">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="ecc4e-110">**Type:** *XRDevice*</span></span>

<span data-ttu-id="ecc4e-111">Per creare un'esperienza di **solo orientamento** o di **scalabilità**verticale, è necessario impostare Unity sul tipo di spazio di rilevamento stazionario.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-111">To build an **orientation-only** or **seated-scale experience**, you must set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="ecc4e-112">In questo modo si imposta il sistema di coordinate globale di Unity per tenere traccia del [frame di riferimento fisso](coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="ecc4e-112">This sets Unity's world coordinate system to track the [stationary frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="ecc4e-113">Nella modalità di rilevamento fisso, il contenuto inserito nell'editor appena davanti alla posizione predefinita della fotocamera (avanti è-Z) verrà visualizzato davanti all'utente all'avvio dell'app.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-113">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="ecc4e-114">**Spazio dei nomi:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="ecc4e-114">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="ecc4e-115">**Tipo:** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="ecc4e-115">**Type:** *InputTracking*</span></span>

<span data-ttu-id="ecc4e-116">Per un' **esperienza solo con orientamento** puro, ad esempio un visualizzatore video di 360 gradi (dove gli aggiornamenti delle intestazioni posizionali potrebbero rovinare l'illusione), è possibile impostare [XR. InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) su true:</span><span class="sxs-lookup"><span data-stu-id="ecc4e-116">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="ecc4e-117">Per un' **esperienza a scalabilità verticale**, per consentire all'utente di ricentrare l'origine in un secondo momento, è possibile chiamare [XR. Metodo InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) :</span><span class="sxs-lookup"><span data-stu-id="ecc4e-117">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a><span data-ttu-id="ecc4e-118">Creazione di un'esperienza di scalabilità o scalabilità in base all'ambiente</span><span class="sxs-lookup"><span data-stu-id="ecc4e-118">Building a standing-scale or room-scale experience</span></span>

<span data-ttu-id="ecc4e-119">**Spazio dei nomi:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="ecc4e-119">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="ecc4e-120">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="ecc4e-120">**Type:** *XRDevice*</span></span>

<span data-ttu-id="ecc4e-121">Per un'esperienza **di scalabilità o** **scalabilità**, è necessario inserire il contenuto relativo alla superficie.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-121">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="ecc4e-122">Si ragiona sul pavimento dell'utente usando la **[fase spaziale](coordinate-systems.md#spatial-coordinate-systems)** , che rappresenta l'origine di livello del piano definita dall'utente e il limite di spazio facoltativo, configurato durante la prima esecuzione.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-122">You reason about the user's floor using the **[spatial stage](coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="ecc4e-123">Per assicurarsi che Unity stia operando con il sistema di coordinate globale a livello di piano, è possibile impostare Unity sul tipo di spazio di rilevamento RoomScale e assicurarsi che il set abbia esito positivo:</span><span class="sxs-lookup"><span data-stu-id="ecc4e-123">To ensure that Unity is operating with its world coordinate system at floor-level, you can set Unity to the RoomScale tracking space type, and ensure that the set succeeds:</span></span>

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* <span data-ttu-id="ecc4e-124">Se SetTrackingSpaceType restituisce true, Unity ha cambiato correttamente il sistema di coordinate globali per tenere traccia del [frame della fase di riferimento](coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="ecc4e-124">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="ecc4e-125">Se SetTrackingSpaceType restituisce false, Unity non è stato in grado di passare al frame della fase di riferimento, probabilmente perché l'utente non ha configurato neanche un piano nel proprio ambiente.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-125">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up even a floor in their environment.</span></span> <span data-ttu-id="ecc4e-126">Questa situazione non è comune, ma può verificarsi se la fase è stata configurata in un'altra stanza e il dispositivo è stato spostato nella stanza corrente senza che l'utente abbia configurato una nuova fase.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-126">This is not common, but can happen if the stage was set up in a different room and the device was moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="ecc4e-127">Quando l'app imposta correttamente il tipo di spazio di rilevamento RoomScale, il contenuto inserito sul piano y = 0 verrà visualizzato sul pavimento.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-127">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="ecc4e-128">L'origine in (0, 0, 0) sarà la posizione specifica del piano in cui l'utente si trovava durante l'installazione della chat room, con-Z che rappresenta la direzione in avanti durante l'installazione.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-128">The origin at (0, 0, 0) will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>

<span data-ttu-id="ecc4e-129">**Spazio dei nomi:** *UnityEngine. EXPERIMENTal. XR*</span><span class="sxs-lookup"><span data-stu-id="ecc4e-129">**Namespace:** *UnityEngine.Experimental.XR*</span></span><br>
<span data-ttu-id="ecc4e-130">**Tipo:** *limite*</span><span class="sxs-lookup"><span data-stu-id="ecc4e-130">**Type:** *Boundary*</span></span>

<span data-ttu-id="ecc4e-131">Nel codice di script è quindi possibile chiamare il metodo TryGetGeometry sul tipo UnityEngine. Experimental. XR. Boundary per ottenere un poligono di limiti, specificando un tipo di limite di TrackedArea.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-131">In script code, you can then call the TryGetGeometry method on your the UnityEngine.Experimental.XR.Boundary type to get a boundary polygon, specifying a boundary type of TrackedArea.</span></span> <span data-ttu-id="ecc4e-132">Se l'utente ha definito un limite (si ottiene un elenco di vertici), si sa che è sicuro fornire un' **esperienza di scalabilità della stanza** all'utente, in cui è possibile aggirare la scena creata.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-132">If the user defined a boundary (you get back a list of vertices), you know it is safe to deliver a **room-scale experience** to the user, where they can walk around the scene you create.</span></span>

<span data-ttu-id="ecc4e-133">Si noti che il sistema eseguirà automaticamente il rendering del limite quando l'utente si avvicina.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-133">Note that the system will automatically render the boundary when the user approaches it.</span></span> <span data-ttu-id="ecc4e-134">L'app non deve usare questo poligono per eseguire il rendering del limite.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-134">Your app does not need to use this polygon to render the boundary itself.</span></span> <span data-ttu-id="ecc4e-135">Tuttavia, è possibile scegliere di disporre gli oggetti della scena utilizzando questo poligono di limiti, per garantire che l'utente possa raggiungere fisicamente tali oggetti senza effettuare il Teleporting:</span><span class="sxs-lookup"><span data-stu-id="ecc4e-135">However, you may choose to lay out your scene objects using this boundary polygon, to ensure the user can physically reach those objects without teleporting:</span></span>

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="ecc4e-136">Creazione di un'esperienza su scala globale</span><span class="sxs-lookup"><span data-stu-id="ecc4e-136">Building a world-scale experience</span></span>

<span data-ttu-id="ecc4e-137">**Spazio dei nomi:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="ecc4e-137">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="ecc4e-138">**Tipo:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="ecc4e-138">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="ecc4e-139">Per esperienze reali su **scala mondiale** su HoloLens che consentono agli utenti di superare i 5 metri, sono necessarie nuove tecniche oltre a quelle usate per le esperienze su scala.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-139">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="ecc4e-140">Una tecnica chiave da usare consiste nel creare un [ancoraggio spaziale](coordinate-systems.md#spatial-anchors) per bloccare un cluster di ologrammi con precisione sul posto nel mondo fisico, indipendentemente dalla distanza di roaming dell'utente e quindi [ritrovare gli ologrammi nelle sessioni successive](coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="ecc4e-140">One key technique you'll use is to create a [spatial anchor](coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, regardless of how far the user has roamed, and then [find those holograms again in later sessions](coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="ecc4e-141">In Unity si crea un ancoraggio spaziale aggiungendo il componente **WorldAnchor** Unity a un GameObject.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-141">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="ecc4e-142">Aggiunta di un ancoraggio globale</span><span class="sxs-lookup"><span data-stu-id="ecc4e-142">Adding a World Anchor</span></span>

<span data-ttu-id="ecc4e-143">Per aggiungere un ancoraggio globale, chiamare AddComponent<WorldAnchor>() sull'oggetto gioco con la trasformazione che si vuole ancorare nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-143">To add a world anchor, call AddComponent<WorldAnchor>() on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="ecc4e-144">La procedura è terminata.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-144">That's it!</span></span> <span data-ttu-id="ecc4e-145">Questo oggetto Game verrà ora ancorato alla posizione corrente nel mondo fisico. è possibile che le coordinate internazionali del mondo Unity vengano modificate leggermente nel tempo per garantire l'allineamento fisico.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-145">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="ecc4e-146">Usare la [persistenza](persistence-in-unity.md) per trovare nuovamente questa posizione ancorata in una sessione di app futura.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-146">Use [persistence](persistence-in-unity.md) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="ecc4e-147">Rimozione di un ancoraggio globale</span><span class="sxs-lookup"><span data-stu-id="ecc4e-147">Removing a World Anchor</span></span>

<span data-ttu-id="ecc4e-148">Se non si vuole più che il GameObject sia bloccato in una posizione fisica del mondo e non si intende trasferirlo in questo frame, è possibile chiamare semplicemente Destroy nel componente World Anchor.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-148">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="ecc4e-149">Se si vuole spostare il GameObject in questo frame, è necessario chiamare DestroyImmediate.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-149">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="ecc4e-150">Trasferimento di una GameObject ancorata globale</span><span class="sxs-lookup"><span data-stu-id="ecc4e-150">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="ecc4e-151">Non è possibile spostare GameObject mentre è presente un ancoraggio globale.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-151">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="ecc4e-152">Se è necessario spostare il GameObject di questo frame, è necessario:</span><span class="sxs-lookup"><span data-stu-id="ecc4e-152">If you need to move the GameObject this frame, you need to:</span></span>
1. <span data-ttu-id="ecc4e-153">DestroyImmediate il componente di ancoraggio globale</span><span class="sxs-lookup"><span data-stu-id="ecc4e-153">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="ecc4e-154">Spostare il GameObject</span><span class="sxs-lookup"><span data-stu-id="ecc4e-154">Move the GameObject</span></span>
3. <span data-ttu-id="ecc4e-155">Aggiungere un nuovo componente di ancoraggio globale a GameObject.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-155">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="ecc4e-156">Gestione delle modifiche apportate a Locatability</span><span class="sxs-lookup"><span data-stu-id="ecc4e-156">Handling Locatability Changes</span></span>

<span data-ttu-id="ecc4e-157">Un WorldAnchor non può essere locatable nel mondo fisico in un determinato momento.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-157">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="ecc4e-158">Se si verifica questa situazione, Unity non aggiornerà la trasformazione dell'oggetto ancorato.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-158">If that occurs, Unity will not be updating the transform of the anchored object.</span></span> <span data-ttu-id="ecc4e-159">Questo può cambiare anche durante l'esecuzione di un'app.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-159">This also can change while an app is running.</span></span> <span data-ttu-id="ecc4e-160">Se non si gestisce la modifica in locatability, l'oggetto non verrà visualizzato nella posizione fisica corretta del mondo.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-160">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="ecc4e-161">Per ricevere notifiche sulle modifiche apportate a locatability:</span><span class="sxs-lookup"><span data-stu-id="ecc4e-161">To be notified about locatability changes:</span></span>
1. <span data-ttu-id="ecc4e-162">Sottoscrivere l'evento OnTrackingChanged</span><span class="sxs-lookup"><span data-stu-id="ecc4e-162">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="ecc4e-163">Gestisci evento</span><span class="sxs-lookup"><span data-stu-id="ecc4e-163">Handle the event</span></span>

<span data-ttu-id="ecc4e-164">L'evento **OnTrackingChanged** verrà chiamato ogni volta che l'ancoraggio spaziale sottostante viene modificato tra uno stato di locatable e non locatable.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-164">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="ecc4e-165">Gestire quindi l'evento:</span><span class="sxs-lookup"><span data-stu-id="ecc4e-165">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="ecc4e-166">Talvolta gli ancoraggi si trovano immediatamente.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-166">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="ecc4e-167">In questo caso, la proprietà individuata dell'ancoraggio verrà impostata su true quando AddComponent<WorldAnchor>() restituisce.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-167">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="ecc4e-168">Di conseguenza, l'evento OnTrackingChanged non verrà attivato.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-168">As a result, the OnTrackingChanged event will not be triggered.</span></span> <span data-ttu-id="ecc4e-169">Un modello pulito consiste nel chiamare il gestore OnTrackingChanged con lo stato individuato iniziale dopo aver collegato un ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-169">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a><span data-ttu-id="ecc4e-170">Condivisione di ancoraggi tra dispositivi</span><span class="sxs-lookup"><span data-stu-id="ecc4e-170">Sharing anchors across devices</span></span>

<span data-ttu-id="ecc4e-171">È possibile usare gli <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">ancoraggi spaziali di Azure</a> per creare un ancoraggio cloud durevole da un WorldAnchor locale, che può essere individuato dall'app su più dispositivi HoloLens, iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-171">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="ecc4e-172">Condividendo un ancoraggio spaziale comune tra più dispositivi, ogni utente può visualizzare il contenuto di cui è stato eseguito il rendering relativo a tale ancoraggio nella stessa posizione fisica.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-172">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="ecc4e-173">Ciò rende possibili esperienze condivise in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-173">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="ecc4e-174">Per iniziare a creare esperienze condivise in Unity, provare le <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guide introduttive Unity Anchors di Azure</a>di 5 minuti.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-174">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="ecc4e-175">Quando si è operativi con i Anchor spaziali di Azure, è possibile <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">creare e individuare ancoraggi in Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="ecc4e-175">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="ecc4e-176">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ecc4e-176">See Also</span></span>
* [<span data-ttu-id="ecc4e-177">Scale Experience</span><span class="sxs-lookup"><span data-stu-id="ecc4e-177">Experience scales</span></span>](coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="ecc4e-178">Fase spaziale</span><span class="sxs-lookup"><span data-stu-id="ecc4e-178">Spatial stage</span></span>](coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="ecc4e-179">Perdita del rilevamento in Unity</span><span class="sxs-lookup"><span data-stu-id="ecc4e-179">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="ecc4e-180">Ancoraggi nello spazio</span><span class="sxs-lookup"><span data-stu-id="ecc4e-180">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="ecc4e-181">Persistenza in Unity</span><span class="sxs-lookup"><span data-stu-id="ecc4e-181">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="ecc4e-182">Esperienze condivise in Unity</span><span class="sxs-lookup"><span data-stu-id="ecc4e-182">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* <span data-ttu-id="ecc4e-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a></span><span class="sxs-lookup"><span data-stu-id="ecc4e-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="ecc4e-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK per Unity</a></span><span class="sxs-lookup"><span data-stu-id="ecc4e-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
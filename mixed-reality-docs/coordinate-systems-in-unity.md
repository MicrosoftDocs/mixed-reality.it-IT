---
title: Sistemi di coordinate in Unity
description: Informazioni su come compilare seduti, permanente, a scalabilità chat room e su scala mondiale mista realtà esperienze in Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema di coordinate, sistema di coordinate spaziale, solo l'orientamento, seduti a scalabilità, la condizione di scalabilità, chat room-scalabilità, mondo della scala, viene posizionata a 360 gradi, e in esecuzione, chat, mondo, scalabilità, posizione, orientamento, Unity, ancoraggio, ancoraggio spaziale, ancoraggio world, bloccato world, blocco a livello mondiale, bloccato corpo, corpo del blocco, rilevamento perdite, locatability, limiti, centrare di nuovo
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605050"
---
# <a name="coordinate-systems-in-unity"></a><span data-ttu-id="24c2b-104">Sistemi di coordinate in Unity</span><span class="sxs-lookup"><span data-stu-id="24c2b-104">Coordinate systems in Unity</span></span>

<span data-ttu-id="24c2b-105">Realtà mista di Windows supporta le App in un'ampia gamma di [esperienza Scale](coordinate-systems.md), dalle App solo l'orientamento e la scala seduto backup tramite chat-ridimensionare le app.</span><span class="sxs-lookup"><span data-stu-id="24c2b-105">Windows Mixed Reality supports apps across a wide range of [experience scales](coordinate-systems.md), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="24c2b-106">HoloLens, consentono di andare oltre e compilare le app su scala mondiale che consentono agli utenti di scorrere oltre 5 metri, esplorazione di un intero piano di un edificio e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="24c2b-106">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="24c2b-107">Il primo passaggio nella creazione di un'esperienza di realtà mista in Unity consiste nel determinare quale [esperienza scalabilità](coordinate-systems.md) destinazione per l'app.</span><span class="sxs-lookup"><span data-stu-id="24c2b-107">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](coordinate-systems.md) your app will target.</span></span>

## <a name="building-an-orientation-only-or-seated-scale-experience"></a><span data-ttu-id="24c2b-108">Creazione di un'esperienza solo orientamento seduto scala o</span><span class="sxs-lookup"><span data-stu-id="24c2b-108">Building an orientation-only or seated-scale experience</span></span>

<span data-ttu-id="24c2b-109">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="24c2b-109">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="24c2b-110">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="24c2b-110">**Type:** *XRDevice*</span></span>

<span data-ttu-id="24c2b-111">Per creare un **orientamento sola** o **esperienza su scala seduto**, è necessario impostare Unity per il fermo rilevamento tipo dello spazio.</span><span class="sxs-lookup"><span data-stu-id="24c2b-111">To build an **orientation-only** or **seated-scale experience**, you must set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="24c2b-112">Sistema di coordinate complessive di Unity per tenere traccia consente di impostare il [fotogramma di riferimento fisso](coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="24c2b-112">This sets Unity's world coordinate system to track the [stationary frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="24c2b-113">Nella modalità di rilevamento fisso, il contenuto inserito nell'editor subito prima di percorso predefinito della camera (in avanti è -Z) verrà visualizzato davanti all'utente quando l'app viene avviata.</span><span class="sxs-lookup"><span data-stu-id="24c2b-113">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="24c2b-114">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="24c2b-114">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="24c2b-115">**Tipo:** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="24c2b-115">**Type:** *InputTracking*</span></span>

<span data-ttu-id="24c2b-116">Per un puro **esperienza solo orientamento** , ad esempio un visualizzatore di video a 360 gradi (in cui gli aggiornamenti di head posizionali potrebbero danneggiare la l'illusione), è quindi possibile impostare [XR. InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) su true:</span><span class="sxs-lookup"><span data-stu-id="24c2b-116">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="24c2b-117">Per un **esperienza su scala seduto**, per consentire all'utente in un secondo momento centrare di nuovo l'origine seduto, è possibile chiamare il [XR. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) metodo:</span><span class="sxs-lookup"><span data-stu-id="24c2b-117">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a><span data-ttu-id="24c2b-118">Creazione di un'esperienza su scala permanente o gradazioni di chat room</span><span class="sxs-lookup"><span data-stu-id="24c2b-118">Building a standing-scale or room-scale experience</span></span>

<span data-ttu-id="24c2b-119">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="24c2b-119">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="24c2b-120">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="24c2b-120">**Type:** *XRDevice*</span></span>

<span data-ttu-id="24c2b-121">Per un **permanente-scalabilità** oppure **esperienza su scala chat room**, è necessario collocare il contenuto relativo al piano.</span><span class="sxs-lookup"><span data-stu-id="24c2b-121">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="24c2b-122">Meglio il suo floor usando il  **[fase spaziali](coordinate-systems.md#spatial-coordinate-systems)**, che rappresenta l'utente definito a livello di parte intera origine e limiti di spazio facoltativo, configurato durante la prima esecuzione.</span><span class="sxs-lookup"><span data-stu-id="24c2b-122">You reason about the user's floor using the **[spatial stage](coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="24c2b-123">Per assicurarsi che funzioni con il sistema di coordinate world floor a livello di Unity, è possibile impostare Unity per il RoomScale rilevamento tipo dello spazio e assicurarsi che il set ha esito positivo:</span><span class="sxs-lookup"><span data-stu-id="24c2b-123">To ensure that Unity is operating with its world coordinate system at floor-level, you can set Unity to the RoomScale tracking space type, and ensure that the set succeeds:</span></span>

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
* <span data-ttu-id="24c2b-124">Se SetTrackingSpaceType restituisce true, Unity è passata relativo sistema di coordinate world per tenere traccia di [fase fotogramma di riferimento](coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="24c2b-124">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="24c2b-125">Se SetTrackingSpaceType restituisce false, Unity non è riuscito a passare alla fase frame di riferimento, probabilmente perché l'utente non ha configurato anche un piano nel proprio ambiente.</span><span class="sxs-lookup"><span data-stu-id="24c2b-125">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up even a floor in their environment.</span></span> <span data-ttu-id="24c2b-126">Non è comune, ma può verificarsi se la fase è stata configurata in una stanza diversi e il dispositivo è stato spostato alla chat corrente senza l'utente che configura una nuova fase.</span><span class="sxs-lookup"><span data-stu-id="24c2b-126">This is not common, but can happen if the stage was set up in a different room and the device was moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="24c2b-127">Una volta che l'app imposta correttamente i RoomScale rilevamento tipo dello spazio, contenuto inserito in y = 0 piano verrà visualizzati sul pavimento.</span><span class="sxs-lookup"><span data-stu-id="24c2b-127">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="24c2b-128">L'origine in corrispondenza (0, 0, 0) sarà la posizione specifica nell'ambiente operativo in cui l'utente si durante l'installazione di chat, con -Z che rappresenta la direzione in avanti che riscontrato durante l'installazione.</span><span class="sxs-lookup"><span data-stu-id="24c2b-128">The origin at (0, 0, 0) will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>

<span data-ttu-id="24c2b-129">**Namespace:** *UnityEngine.Experimental.XR*</span><span class="sxs-lookup"><span data-stu-id="24c2b-129">**Namespace:** *UnityEngine.Experimental.XR*</span></span><br>
<span data-ttu-id="24c2b-130">**Tipo:** *Boundary*</span><span class="sxs-lookup"><span data-stu-id="24c2b-130">**Type:** *Boundary*</span></span>

<span data-ttu-id="24c2b-131">Nel codice di script, è quindi possibile chiamare il metodo TryGetGeometry per l'utente è il tipo UnityEngine.Experimental.XR.Boundary per ottenere un poligono di confine, che specifica un tipo di limite di TrackedArea.</span><span class="sxs-lookup"><span data-stu-id="24c2b-131">In script code, you can then call the TryGetGeometry method on your the UnityEngine.Experimental.XR.Boundary type to get a boundary polygon, specifying a boundary type of TrackedArea.</span></span> <span data-ttu-id="24c2b-132">Se l'utente ha definito un limite (verrà restituito un elenco di vertici), si saprà già sia sicuro offrire una **esperienza su scala chat room** all'utente, in cui sono inoltre informazioni dettagliate per la scena creare.</span><span class="sxs-lookup"><span data-stu-id="24c2b-132">If the user defined a boundary (you get back a list of vertices), you know it is safe to deliver a **room-scale experience** to the user, where they can walk around the scene you create.</span></span>

<span data-ttu-id="24c2b-133">Si noti che il sistema esegue il rendering automatico il limite quando l'utente si avvicina.</span><span class="sxs-lookup"><span data-stu-id="24c2b-133">Note that the system will automatically render the boundary when the user approaches it.</span></span> <span data-ttu-id="24c2b-134">L'app non dovrà utilizzare questo poligono per il rendering del limite se stesso.</span><span class="sxs-lookup"><span data-stu-id="24c2b-134">Your app does not need to use this polygon to render the boundary itself.</span></span> <span data-ttu-id="24c2b-135">Tuttavia, è possibile scegliere di disporre gli oggetti di scena usando questo poligono di confine, per garantire che l'utente possa raggiungere fisicamente gli oggetti senza teleporting:</span><span class="sxs-lookup"><span data-stu-id="24c2b-135">However, you may choose to lay out your scene objects using this boundary polygon, to ensure the user can physically reach those objects without teleporting:</span></span>

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="24c2b-136">Creazione di un'esperienza su scala mondiale</span><span class="sxs-lookup"><span data-stu-id="24c2b-136">Building a world-scale experience</span></span>

<span data-ttu-id="24c2b-137">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="24c2b-137">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="24c2b-138">**Tipo:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="24c2b-138">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="24c2b-139">Per true **esperienze su scala mondiale** in HoloLens che consentono agli utenti di vagare oltre 5 metri, sarà necessario nuove tecniche oltre a quelli usati per le esperienze su scala chat room.</span><span class="sxs-lookup"><span data-stu-id="24c2b-139">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="24c2b-140">Una tecnica fondamentale userai consiste nel creare un [ancoraggio spaziale](coordinate-systems.md#spatial-anchors) per bloccare un cluster di vntana con precisione in posti del mondo fisico, indipendentemente dal fatto fino a quando l'utente dispone di roaming e quindi [trovare tali vntana nuovamente in un secondo momento le sessioni](coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="24c2b-140">One key technique you'll use is to create a [spatial anchor](coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, regardless of how far the user has roamed, and then [find those holograms again in later sessions](coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="24c2b-141">In Unity, un punto di ancoraggio spaziale viene creato aggiungendo i **WorldAnchor** componente di Unity al GameObject.</span><span class="sxs-lookup"><span data-stu-id="24c2b-141">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="24c2b-142">Aggiunta di un punto di ancoraggio del mondo</span><span class="sxs-lookup"><span data-stu-id="24c2b-142">Adding a World Anchor</span></span>

<span data-ttu-id="24c2b-143">Per aggiungere un punto di ancoraggio del mondo, chiamare AddComponent<WorldAnchor>() per l'oggetto gioco con la trasformazione che si desidera ancorare nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="24c2b-143">To add a world anchor, call AddComponent<WorldAnchor>() on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="24c2b-144">La procedura è terminata.</span><span class="sxs-lookup"><span data-stu-id="24c2b-144">That's it!</span></span> <span data-ttu-id="24c2b-145">L'oggetto gioco verrà ora ancorata alla posizione corrente nel mondo fisico, è possibile visualizzare le relative coordinate world Unity modificare leggermente nel corso del tempo per verificare che tale allineamento fisico.</span><span class="sxs-lookup"><span data-stu-id="24c2b-145">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="24c2b-146">Uso [persistenza](persistence-in-unity.md) a trovarlo ancorata percorso nuovamente in una sessione di app future.</span><span class="sxs-lookup"><span data-stu-id="24c2b-146">Use [persistence](persistence-in-unity.md) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="24c2b-147">Rimozione di un punto di ancoraggio del mondo</span><span class="sxs-lookup"><span data-stu-id="24c2b-147">Removing a World Anchor</span></span>

<span data-ttu-id="24c2b-148">Se desidera che gli elementi GameObject bloccato in una posizione del mondo fisico e non prevede sullo spostamento di questo frame, è possibile chiamare semplicemente Destroy sul componente World ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="24c2b-148">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="24c2b-149">Se si desidera spostare gli elementi GameObject questo frame, è necessario chiamare invece DestroyImmediate.</span><span class="sxs-lookup"><span data-stu-id="24c2b-149">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="24c2b-150">Lo spostamento di un mondo ancorata GameObject</span><span class="sxs-lookup"><span data-stu-id="24c2b-150">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="24c2b-151">GameObject non è possibile spostare un punto di ancoraggio World posizionato su di esso.</span><span class="sxs-lookup"><span data-stu-id="24c2b-151">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="24c2b-152">Se è necessario spostare gli elementi GameObject questo frame, è necessario:</span><span class="sxs-lookup"><span data-stu-id="24c2b-152">If you need to move the GameObject this frame, you need to:</span></span>
1. <span data-ttu-id="24c2b-153">Il componente World ancoraggio DestroyImmediate</span><span class="sxs-lookup"><span data-stu-id="24c2b-153">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="24c2b-154">Spostare gli elementi GameObject</span><span class="sxs-lookup"><span data-stu-id="24c2b-154">Move the GameObject</span></span>
3. <span data-ttu-id="24c2b-155">Aggiungere un nuovo componente World ancoraggio per gli elementi GameObject.</span><span class="sxs-lookup"><span data-stu-id="24c2b-155">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="24c2b-156">Gestione delle modifiche Locatability</span><span class="sxs-lookup"><span data-stu-id="24c2b-156">Handling Locatability Changes</span></span>

<span data-ttu-id="24c2b-157">Un WorldAnchor potrebbe non essere individuabili nel mondo fisico a un punto nel tempo.</span><span class="sxs-lookup"><span data-stu-id="24c2b-157">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="24c2b-158">In tal caso, Unity non aggiornerà la trasformazione dell'oggetto ancorato.</span><span class="sxs-lookup"><span data-stu-id="24c2b-158">If that occurs, Unity will not be updating the transform of the anchored object.</span></span> <span data-ttu-id="24c2b-159">Questo inoltre può cambiare durante l'esecuzione di un'app.</span><span class="sxs-lookup"><span data-stu-id="24c2b-159">This also can change while an app is running.</span></span> <span data-ttu-id="24c2b-160">L'incapacità di gestire la modifica in locatability causerà l'oggetto non viene visualizzato nella posizione corretta nel mondo fisica.</span><span class="sxs-lookup"><span data-stu-id="24c2b-160">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="24c2b-161">Per ricevere una notifica sulle modifiche locatability:</span><span class="sxs-lookup"><span data-stu-id="24c2b-161">To be notified about locatability changes:</span></span>
1. <span data-ttu-id="24c2b-162">Sottoscrivere l'evento OnTrackingChanged</span><span class="sxs-lookup"><span data-stu-id="24c2b-162">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="24c2b-163">Gestire l'evento</span><span class="sxs-lookup"><span data-stu-id="24c2b-163">Handle the event</span></span>

<span data-ttu-id="24c2b-164">Il **OnTrackingChanged** eventi verranno chiamato ogni volta che il punto di ancoraggio spaziale sottostante viene modificato tra uno stato di essere individuabili e non è individuabile.</span><span class="sxs-lookup"><span data-stu-id="24c2b-164">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="24c2b-165">Gestire l'evento:</span><span class="sxs-lookup"><span data-stu-id="24c2b-165">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="24c2b-166">In alcuni casi gli ancoraggi si trovano immediatamente.</span><span class="sxs-lookup"><span data-stu-id="24c2b-166">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="24c2b-167">In questo caso, isLocated dell'ancoraggio sarà essere impostata su true quando AddComponent<WorldAnchor>() restituisce.</span><span class="sxs-lookup"><span data-stu-id="24c2b-167">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="24c2b-168">Di conseguenza, l'evento OnTrackingChanged non verrà attivata.</span><span class="sxs-lookup"><span data-stu-id="24c2b-168">As a result, the OnTrackingChanged event will not be triggered.</span></span> <span data-ttu-id="24c2b-169">Un modello pulito, è possibile chiamare il gestore OnTrackingChanged con lo stato IsLocated iniziale dopo aver collegato un ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="24c2b-169">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a><span data-ttu-id="24c2b-170">Condivisione Anchor tra i dispositivi</span><span class="sxs-lookup"><span data-stu-id="24c2b-170">Sharing anchors across devices</span></span>

<span data-ttu-id="24c2b-171">È possibile usare <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Anchor spaziali Azure</a> per creare un punto di ancoraggio cloud permanenti da un WorldAnchor locale, che consente quindi di individuare l'app in più HoloLens, dispositivi iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="24c2b-171">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="24c2b-172">Condividendo un ancoraggio spaziale comune tra più dispositivi, ogni utente può visualizzare il contenuto sottoposto a rendering relativo tale ancoraggio nella stessa posizione fisica.</span><span class="sxs-lookup"><span data-stu-id="24c2b-172">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="24c2b-173">Ciò consente esperienze condivise in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="24c2b-173">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="24c2b-174">Per iniziare a creare esperienze condivise in Unity, provare i 5 minuti <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guide introduttive di Azure spaziali Anchor Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="24c2b-174">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="24c2b-175">Quando si è in esecuzione con Azure Anchor spaziale, è possibile quindi <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">creare e individuare gli ancoraggi in Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="24c2b-175">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="24c2b-176">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="24c2b-176">See Also</span></span>
* [<span data-ttu-id="24c2b-177">Esperienza scale</span><span class="sxs-lookup"><span data-stu-id="24c2b-177">Experience scales</span></span>](coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="24c2b-178">Fase spaziali</span><span class="sxs-lookup"><span data-stu-id="24c2b-178">Spatial stage</span></span>](coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="24c2b-179">Perdita di rilevamento in Unity</span><span class="sxs-lookup"><span data-stu-id="24c2b-179">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="24c2b-180">Ancoraggi spaziali</span><span class="sxs-lookup"><span data-stu-id="24c2b-180">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="24c2b-181">Persistenza in Unity</span><span class="sxs-lookup"><span data-stu-id="24c2b-181">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="24c2b-182">Esperienze condivise in Unity</span><span class="sxs-lookup"><span data-stu-id="24c2b-182">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* <span data-ttu-id="24c2b-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Anchor spaziali</a></span><span class="sxs-lookup"><span data-stu-id="24c2b-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="24c2b-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Ancoraggi spaziali Azure SDK per Unity</a></span><span class="sxs-lookup"><span data-stu-id="24c2b-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
---
title: Persistenza in Unity
description: Persistenza consente agli utenti di aggiungere singoli vntana o un'area di lavoro ovunque desiderino e quindi trovare dove si aspettano su molti in un secondo momento Usa dell'app.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, persistenza, Unity
ms.openlocfilehash: b6a67e52b3a5ce724a90eb1a479c5eda74b0c4cb
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605079"
---
# <a name="persistence-in-unity"></a><span data-ttu-id="12ee4-104">Persistenza in Unity</span><span class="sxs-lookup"><span data-stu-id="12ee4-104">Persistence in Unity</span></span>

<span data-ttu-id="12ee4-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span><span class="sxs-lookup"><span data-stu-id="12ee4-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="12ee4-106">**Classe:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="12ee4-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="12ee4-107">Il WorldAnchorStore è la chiave per la creazione di esperienze holographic dove vntana rimangono nelle posizioni reali specifico tra più istanze dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="12ee4-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="12ee4-108">In questo modo gli utenti aggiungono vntana singoli o un'area di lavoro ogni volta che serve e quindi trovare in un secondo momento in cui si aspettano su molti utilizzi delle app.</span><span class="sxs-lookup"><span data-stu-id="12ee4-108">This lets your users pin individual holograms or a workspace wherever they want it, and then find it later where they expect over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="12ee4-109">Come rendere permanente vntana tra le sessioni</span><span class="sxs-lookup"><span data-stu-id="12ee4-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="12ee4-110">Il WorldAnchorStore consentirà di rendere persistente il percorso del WorldAnchor tra le sessioni.</span><span class="sxs-lookup"><span data-stu-id="12ee4-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="12ee4-111">Per rendere effettivamente persistente vntana tra le sessioni, dovrai separatamente tenere traccia del Gameobject che usano un punto di ancoraggio world particolare.</span><span class="sxs-lookup"><span data-stu-id="12ee4-111">To actually persist holograms across sessions, you will need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="12ee4-112">È spesso opportuno creare un GameObject radice con un punto di ancoraggio del mondo e avere elementi figlio ancorati vntana dalla funzione con un offset della posizione locale.</span><span class="sxs-lookup"><span data-stu-id="12ee4-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="12ee4-113">Per caricare vntana dalle sessioni precedenti:</span><span class="sxs-lookup"><span data-stu-id="12ee4-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="12ee4-114">Ottenere il WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="12ee4-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="12ee4-115">Caricare i dati dell'app relativi in base all'ancoraggio mondo che fornisce l'id del punto di ancoraggio il mondo</span><span class="sxs-lookup"><span data-stu-id="12ee4-115">Load app data relating to the world anchor which gives you the id of the world anchor</span></span>
3. <span data-ttu-id="12ee4-116">Caricare un ancoraggio world dal relativo id</span><span class="sxs-lookup"><span data-stu-id="12ee4-116">Load a world anchor from its id</span></span>

<span data-ttu-id="12ee4-117">Per salvare vntana per le sessioni future:</span><span class="sxs-lookup"><span data-stu-id="12ee4-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="12ee4-118">Ottenere il WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="12ee4-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="12ee4-119">Salvare un ancoraggio world specificando un id</span><span class="sxs-lookup"><span data-stu-id="12ee4-119">Save a world anchor specifying an id</span></span>
3. <span data-ttu-id="12ee4-120">Salvare i dati dell'app relativi in base all'ancoraggio mondiale insieme a un id</span><span class="sxs-lookup"><span data-stu-id="12ee4-120">Save app data relating to the world anchor along with an id</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="12ee4-121">Introduzione di WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="12ee4-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="12ee4-122">È consigliabile mantenere un riferimento al WorldAnchorStore intorno quindi sappiamo che siamo pronti passare quando si vuole eseguire un'operazione.</span><span class="sxs-lookup"><span data-stu-id="12ee4-122">We will want to keep a reference to the WorldAnchorStore around so we know we are ready to go when we want to perform an operation.</span></span> <span data-ttu-id="12ee4-123">Poiché si tratta di una chiamata async, potenzialmente appena start, da chiamare</span><span class="sxs-lookup"><span data-stu-id="12ee4-123">Since this is an async call, potentially as soon as start up, we want to call</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="12ee4-124">In questo caso, StoreLoaded è il nostro gestore dopo il WorldAnchorStore ha completato il caricamento:</span><span class="sxs-lookup"><span data-stu-id="12ee4-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="12ee4-125">È ora disponibile un riferimento a WorldAnchorStore che verrà usato per salvare e caricare gli ancoraggi World specifico.</span><span class="sxs-lookup"><span data-stu-id="12ee4-125">We now have a reference to the WorldAnchorStore which we will use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="12ee4-126">Salvataggio di un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="12ee4-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="12ee4-127">Per salvare, è sufficiente per assegnare un nome di ciò che si sta salvando e lo associo al WorldAnchor ottenuto prima di quando si desidera salvare.</span><span class="sxs-lookup"><span data-stu-id="12ee4-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="12ee4-128">Nota: tentativo di salvare gli due ancoraggi sulla stessa stringa avrà esito negativo (archivio. Salva restituirà false).</span><span class="sxs-lookup"><span data-stu-id="12ee4-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="12ee4-129">È necessario eliminare il salvataggio precedente prima di salvare una nuova:</span><span class="sxs-lookup"><span data-stu-id="12ee4-129">You need to Delete the previous save before saving the new one:</span></span>

```
private void SaveGame()
{
       // Save data about holograms positioned by this world anchor
       if (!this.savedRoot) // Only Save the root once
       {
              this.savedRoot = this.store.Save("rootGameObject", anchor);
              Assert(this.savedRoot);
       }
}
```

### <a name="loading-a-worldanchor"></a><span data-ttu-id="12ee4-130">Il caricamento di un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="12ee4-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="12ee4-131">E da caricare:</span><span class="sxs-lookup"><span data-stu-id="12ee4-131">And to load:</span></span>

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

<span data-ttu-id="12ee4-132">È inoltre possibile usare archivio. Delete () per rimuovere un ancoraggio che viene salvati in precedenza e archivio. Clear () per rimuovere tutti i dati salvati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="12ee4-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="12ee4-133">L'enumerazione dei punti di ancoraggio esistente</span><span class="sxs-lookup"><span data-stu-id="12ee4-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="12ee4-134">Per individuare gli ancoraggi archiviati in precedenza, chiamare GetAllIds.</span><span class="sxs-lookup"><span data-stu-id="12ee4-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="12ee4-135">Ologrammi persistenza per più dispositivi</span><span class="sxs-lookup"><span data-stu-id="12ee4-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="12ee4-136">È possibile usare <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Anchor spaziali Azure</a> per creare un punto di ancoraggio cloud permanenti da un WorldAnchor locale, che l'app consente quindi di individuare in più HoloLens, dispositivi iOS e Android, anche se questi dispositivi non sono presenti contemporaneamente allo stesso ora.</span><span class="sxs-lookup"><span data-stu-id="12ee4-136">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices are not present together at the same time.</span></span>  <span data-ttu-id="12ee4-137">Poiché gli ancoraggi cloud sono persistenti, più dispositivi nel corso del tempo ogni noterà contenuto sottoposto a rendering relativo tale ancoraggio nella stessa posizione fisica.</span><span class="sxs-lookup"><span data-stu-id="12ee4-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="12ee4-138">Per iniziare a creare esperienze condivise in Unity, provare i 5 minuti <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guide introduttive di Azure spaziali Anchor Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="12ee4-138">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="12ee4-139">Quando si è in esecuzione con Azure Anchor spaziale, è possibile quindi <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">creare e individuare gli ancoraggi in Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="12ee4-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="12ee4-140">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="12ee4-140">See Also</span></span>
* [<span data-ttu-id="12ee4-141">Persistenza di ancoraggio spaziali</span><span class="sxs-lookup"><span data-stu-id="12ee4-141">Spatial anchor persistence</span></span>](coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="12ee4-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Anchor spaziali</a></span><span class="sxs-lookup"><span data-stu-id="12ee4-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="12ee4-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Ancoraggi spaziali Azure SDK per Unity</a></span><span class="sxs-lookup"><span data-stu-id="12ee4-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>

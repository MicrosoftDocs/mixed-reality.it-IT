---
title: Trasferimenti di ancoraggio locali in Unity
description: Trasferire gli ancoraggi tra più dispositivi HoloLens in un'applicazione Unity.
author: fieldsjacksong
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: Sharing, Anchor, WorldAnchor, MR sharing 250, WorldAnchorTransferBatch, SpatialPerception, Transfer, local Anchor Transfer, Anchor Export, Anchor import
ms.openlocfilehash: fd071f736add094fd65ae4d889f8008eefd8515d
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278059"
---
# <a name="local-anchor-transfers-in-unity"></a><span data-ttu-id="0a0a2-104">Trasferimenti di ancoraggio locali in Unity</span><span class="sxs-lookup"><span data-stu-id="0a0a2-104">Local anchor transfers in Unity</span></span>

<span data-ttu-id="0a0a2-105">Nei casi in cui non è possibile usare gli <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">ancoraggi spaziali di Azure</a>, i trasferimenti di ancoraggio locali consentono a un dispositivo HoloLens di esportare un ancoraggio per l'importazione da parte di un secondo dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0a0a2-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="0a0a2-106">I trasferimenti di ancoraggio locali forniscono un richiamo di ancoraggio meno affidabile rispetto agli <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">ancoraggi spaziali di Azure</a>e i dispositivi iOS e Android non sono supportati da questo approccio.</span><span class="sxs-lookup"><span data-stu-id="0a0a2-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

### <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="0a0a2-107">Impostazione della funzionalità SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="0a0a2-107">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="0a0a2-108">Per consentire a un'app di trasferire ancoraggi spaziali, è necessario abilitare la funzionalità *SpatialPerception* .</span><span class="sxs-lookup"><span data-stu-id="0a0a2-108">In order for an app to transfer spatial anchors, the *SpatialPerception* capability must be enabled.</span></span>

<span data-ttu-id="0a0a2-109">Come abilitare la funzionalità *SpatialPerception* :</span><span class="sxs-lookup"><span data-stu-id="0a0a2-109">How to enable the *SpatialPerception* capability:</span></span>
1. <span data-ttu-id="0a0a2-110">Nell'editor di Unity aprire il riquadro **"Impostazioni lettore"** (modificare > impostazioni progetto > lettore)</span><span class="sxs-lookup"><span data-stu-id="0a0a2-110">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="0a0a2-111">Fare clic sulla scheda **"Windows Store"**</span><span class="sxs-lookup"><span data-stu-id="0a0a2-111">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="0a0a2-112">Espandere **"impostazioni di pubblicazione"** e selezionare la funzionalità **"SpatialPerception"** nell'elenco **"funzionalità"**</span><span class="sxs-lookup"><span data-stu-id="0a0a2-112">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

>[!NOTE]
><span data-ttu-id="0a0a2-113">Se il progetto Unity è già stato esportato in una soluzione di Visual Studio, sarà necessario eseguire l'esportazione in una nuova cartella o [impostare manualmente questa funzionalità in appxmanifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span><span class="sxs-lookup"><span data-stu-id="0a0a2-113">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

### <a name="anchor-transfer"></a><span data-ttu-id="0a0a2-114">Trasferimento di ancoraggio</span><span class="sxs-lookup"><span data-stu-id="0a0a2-114">Anchor Transfer</span></span>

<span data-ttu-id="0a0a2-115">**Spazio dei nomi:** *UnityEngine. XR. WSA. sharing*</span><span class="sxs-lookup"><span data-stu-id="0a0a2-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span></span><br>
<span data-ttu-id="0a0a2-116">**Tipo**: *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="0a0a2-116">**Type**: *WorldAnchorTransferBatch*</span></span>

<span data-ttu-id="0a0a2-117">Per trasferire un [WorldAnchor](coordinate-systems-in-unity.md), è necessario stabilire l'ancoraggio da trasferire.</span><span class="sxs-lookup"><span data-stu-id="0a0a2-117">To transfer a [WorldAnchor](coordinate-systems-in-unity.md), one must establish the anchor to be transferred.</span></span> <span data-ttu-id="0a0a2-118">L'utente di un HoloLens analizza l'ambiente e sceglie manualmente o a livello di codice un punto nello spazio come ancoraggio per l'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="0a0a2-118">The user of one HoloLens scans their environment and either manually or programmatically chooses a point in space to be the Anchor for the shared experience.</span></span> <span data-ttu-id="0a0a2-119">I dati che rappresentano questo punto possono quindi essere serializzati e trasmessi agli altri dispositivi che condividono nell'esperienza.</span><span class="sxs-lookup"><span data-stu-id="0a0a2-119">The data that represents this point can then be serialized and transmitted to the other devices that are sharing in the experience.</span></span> <span data-ttu-id="0a0a2-120">Ogni dispositivo deserializza quindi i dati di ancoraggio e tenta di individuare il punto nello spazio.</span><span class="sxs-lookup"><span data-stu-id="0a0a2-120">Each device then de-serializes the anchor data and attempts to locate that point in space.</span></span> <span data-ttu-id="0a0a2-121">Per il corretto funzionamento del trasferimento di ancoraggio, è necessario che ogni dispositivo abbia eseguito una scansione sufficiente dell'ambiente, in modo che sia possibile identificare il punto rappresentato dall'ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="0a0a2-121">In order for Anchor Transfer to work, each device must have scanned in enough of the environment such that the point represented by the anchor can be identified.</span></span>

### <a name="setup"></a><span data-ttu-id="0a0a2-122">Programma di installazione</span><span class="sxs-lookup"><span data-stu-id="0a0a2-122">Setup</span></span>

<span data-ttu-id="0a0a2-123">Il codice di esempio in questa pagina contiene alcuni campi che dovranno essere inizializzati:</span><span class="sxs-lookup"><span data-stu-id="0a0a2-123">The sample code on this page has a few fields that will need to be initialized:</span></span>
1. <span data-ttu-id="0a0a2-124">*GameObject rootGameObject* è un *GameObject* in Unity in cui è presente un componente *WorldAnchor* .</span><span class="sxs-lookup"><span data-stu-id="0a0a2-124">*GameObject rootGameObject* is a *GameObject* in Unity that has a *WorldAnchor* Component on it.</span></span> <span data-ttu-id="0a0a2-125">Un utente nell'esperienza condivisa inserisce questo *GameObject* ed Esporta i dati negli altri utenti.</span><span class="sxs-lookup"><span data-stu-id="0a0a2-125">One user in the shared experience will place this *GameObject* and export the data to the other users.</span></span>
2. <span data-ttu-id="0a0a2-126">*WorldAnchor gameRootAnchor* è *UnityEngine. XR. WSA. WorldAnchor* che si trova in *rootGameObject*.</span><span class="sxs-lookup"><span data-stu-id="0a0a2-126">*WorldAnchor gameRootAnchor* is the *UnityEngine.XR.WSA.WorldAnchor* that is on *rootGameObject*.</span></span>
3. <span data-ttu-id="0a0a2-127">*byte [] importedData* è una matrice di byte per l'ancoraggio serializzato che ogni client riceve sulla rete.</span><span class="sxs-lookup"><span data-stu-id="0a0a2-127">*byte[] importedData* is a byte array for the serialized anchor each client is receiving over the network.</span></span>

```
public GameObject rootGameObject;
private UnityEngine.XR.WSA.WorldAnchor gameRootAnchor;

void Start ()
{
    gameRootAnchor = rootGameObject.GetComponent<UnityEngine.XR.WSA.WorldAnchor>();

    if (gameRootAnchor == null)
    {
        gameRootAnchor = rootGameObject.AddComponent<UnityEngine.XR.WSA.WorldAnchor>();
    }
}
```

### <a name="exporting"></a><span data-ttu-id="0a0a2-128">Esportazione</span><span class="sxs-lookup"><span data-stu-id="0a0a2-128">Exporting</span></span>

<span data-ttu-id="0a0a2-129">Per eseguire l'esportazione, è sufficiente un *WorldAnchor* e per sapere cosa verrà chiamato in modo da renderlo utile per l'app ricevente.</span><span class="sxs-lookup"><span data-stu-id="0a0a2-129">To export, we just need a *WorldAnchor* and to know what we will call it such that it makes sense for the receiving app.</span></span> <span data-ttu-id="0a0a2-130">Un client nell'esperienza condivisa eseguirà questa procedura per esportare l'ancoraggio condiviso:</span><span class="sxs-lookup"><span data-stu-id="0a0a2-130">One client in the shared experience will perform these steps to export the shared anchor:</span></span>
1. <span data-ttu-id="0a0a2-131">Creare un *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="0a0a2-131">Create a *WorldAnchorTransferBatch*</span></span>
2. <span data-ttu-id="0a0a2-132">Aggiungere il *WorldAnchors* da trasferire</span><span class="sxs-lookup"><span data-stu-id="0a0a2-132">Add the *WorldAnchors* to transfer</span></span>
3. <span data-ttu-id="0a0a2-133">Inizia l'esportazione</span><span class="sxs-lookup"><span data-stu-id="0a0a2-133">Begin the export</span></span>
4. <span data-ttu-id="0a0a2-134">Gestisci l'evento *OnExportDataAvailable* quando i dati diventano disponibili</span><span class="sxs-lookup"><span data-stu-id="0a0a2-134">Handle the *OnExportDataAvailable* event as data becomes available</span></span>
5. <span data-ttu-id="0a0a2-135">Gestisci evento *OnExportComplete*</span><span class="sxs-lookup"><span data-stu-id="0a0a2-135">Handle the *OnExportComplete* event</span></span>

<span data-ttu-id="0a0a2-136">Viene creato un *WorldAnchorTransferBatch* per incapsulare gli elementi che verranno trasferiti e quindi esportati in byte:</span><span class="sxs-lookup"><span data-stu-id="0a0a2-136">We create a *WorldAnchorTransferBatch* to encapsulate what we will be transferring and then export that into bytes:</span></span>

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

<span data-ttu-id="0a0a2-137">Quando i dati diventano disponibili, inviare i byte al client o al buffer perché i segmenti di dati sono disponibili e inviarli con qualsiasi mezzo:</span><span class="sxs-lookup"><span data-stu-id="0a0a2-137">As data becomes available, send the bytes to the client or buffer as segments of data is available and send through whatever means desired:</span></span>

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

<span data-ttu-id="0a0a2-138">Al termine dell'esportazione, se i dati sono stati trasferiti e la serializzazione non è riuscita, indicare al client di rimuovere i dati.</span><span class="sxs-lookup"><span data-stu-id="0a0a2-138">Once the export is complete, if we have been transferring data and serialization failed, tell the client to discard the data.</span></span> <span data-ttu-id="0a0a2-139">Se la serializzazione ha avuto esito positivo, indicare al client che tutti i dati sono stati trasferiti e che è possibile avviare l'importazione:</span><span class="sxs-lookup"><span data-stu-id="0a0a2-139">If the serialization succeeded, tell the client that all data has been transferred and importing can start:</span></span>

```
private void OnExportComplete(SerializationCompletionReason completionReason)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        SendExportFailedToClient();
    }
    else
    {
        SendExportSucceededToClient();
    }
}
```

### <a name="importing"></a><span data-ttu-id="0a0a2-140">Importazione</span><span class="sxs-lookup"><span data-stu-id="0a0a2-140">Importing</span></span>

<span data-ttu-id="0a0a2-141">Dopo aver ricevuto tutti i byte dal mittente, è possibile importare di nuovo i dati in un *WorldAnchorTransferBatch* e bloccare l'oggetto del gioco radice nella stessa posizione fisica.</span><span class="sxs-lookup"><span data-stu-id="0a0a2-141">After receiving all of the bytes from the sender, we can import the data back into a *WorldAnchorTransferBatch* and lock our root game object into the same physical location.</span></span> <span data-ttu-id="0a0a2-142">Nota: l'importazione a volte avrà esito negativo e deve essere riprovata:</span><span class="sxs-lookup"><span data-stu-id="0a0a2-142">Note: import will sometimes transiently fail and needs to be retried:</span></span>

```
// This byte array should have been updated over the network from TransferDataToClient
private byte[] importedData;
private int retryCount = 3;

private void ImportRootGameObject()
{
    WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
}

private void OnImportComplete(SerializationCompletionReason completionReason, WorldAnchorTransferBatch deserializedTransferBatch)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        Debug.Log("Failed to import: " + completionReason.ToString());
        if (retryCount > 0)
        {
            retryCount--;
            WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
        }
        return;
    }

    this.gameRootAnchor = deserializedTransferBatch.LockObject("gameRoot", this.rootGameObject);
}
```

<span data-ttu-id="0a0a2-143">Dopo che un *GameObject* è stato bloccato tramite la chiamata *lockobject* , avrà un *WorldAnchor* che lo manterrà nella stessa posizione fisica del mondo, ma potrebbe trovarsi in una posizione diversa nello spazio delle coordinate di Unity rispetto ad altri utenti.</span><span class="sxs-lookup"><span data-stu-id="0a0a2-143">After a *GameObject* is locked via the *LockObject* call, it will have a *WorldAnchor* which will keep it in the same physical position in the world, but it may be at a different location in the Unity coordinate space than other users.</span></span>


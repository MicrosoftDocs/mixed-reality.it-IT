---
title: Trasferimenti di ancoraggio locale in Unity
description: Trasferire gli ancoraggi tra più dispositivi HoloLens in un'applicazione Unity.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: Condivisione, ancoraggio, WorldAnchor, MR condivisione 250, WorldAnchorTransferBatch, SpatialPerception, transfer, trasferimento locale di ancoraggio, esportazione di ancoraggio, importazione di ancoraggio
ms.openlocfilehash: 82bcd07417fd5aa1b265ebc3c8edc939101dd783
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605059"
---
# <a name="local-anchor-transfers-in-unity"></a><span data-ttu-id="fa65e-104">Trasferimenti di ancoraggio locale in Unity</span><span class="sxs-lookup"><span data-stu-id="fa65e-104">Local anchor transfers in Unity</span></span>

<span data-ttu-id="fa65e-105">In situazioni in cui non è possibile usare <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Anchor spaziali Azure</a>, trasferimenti di ancoraggio locale abilitare un dispositivo HoloLens esportare un ancoraggio per essere importati da un secondo dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fa65e-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="fa65e-106">I trasferimenti di ancoraggio locale forniscono richiamo ancoraggio meno affidabile rispetto <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Anchor spaziali Azure</a>, e dispositivi iOS e Android non sono supportati da questo approccio.</span><span class="sxs-lookup"><span data-stu-id="fa65e-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

### <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="fa65e-107">Impostare la funzionalità SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="fa65e-107">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="fa65e-108">Affinché un'app di trasferire gli ancoraggi spaziali, il *SpatialPerception* deve essere attivata.</span><span class="sxs-lookup"><span data-stu-id="fa65e-108">In order for an app to transfer spatial anchors, the *SpatialPerception* capability must be enabled.</span></span>

<span data-ttu-id="fa65e-109">Come abilitare il *SpatialPerception* funzionalità:</span><span class="sxs-lookup"><span data-stu-id="fa65e-109">How to enable the *SpatialPerception* capability:</span></span>
1. <span data-ttu-id="fa65e-110">Nell'Editor di Unity, aprire il **"Windows Media Player Settings"** riquadro (Modifica > Impostazioni di progetto > Windows Media Player)</span><span class="sxs-lookup"><span data-stu-id="fa65e-110">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="fa65e-111">Fare clic sui **"Windows Store"** scheda</span><span class="sxs-lookup"><span data-stu-id="fa65e-111">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="fa65e-112">Espandere **"Impostazioni di pubblicazione"** e selezionare il **"SpatialPerception"** funzionalità nel **"Funzionalità"** elenco</span><span class="sxs-lookup"><span data-stu-id="fa65e-112">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

>[!NOTE]
><span data-ttu-id="fa65e-113">Se è già stato esportato il progetto di Unity a una soluzione di Visual Studio, è necessario esportare in una nuova cartella o manualmente [impostare questa funzionalità in AppxManifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span><span class="sxs-lookup"><span data-stu-id="fa65e-113">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

### <a name="anchor-transfer"></a><span data-ttu-id="fa65e-114">Trasferimento di ancoraggio</span><span class="sxs-lookup"><span data-stu-id="fa65e-114">Anchor Transfer</span></span>

<span data-ttu-id="fa65e-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span><span class="sxs-lookup"><span data-stu-id="fa65e-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span></span><br>
<span data-ttu-id="fa65e-116">**Tipo**: *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="fa65e-116">**Type**: *WorldAnchorTransferBatch*</span></span>

<span data-ttu-id="fa65e-117">Per trasferire una [WorldAnchor](coordinate-systems-in-unity.md), uno deve essere stabilita l'ancoraggio da trasferire.</span><span class="sxs-lookup"><span data-stu-id="fa65e-117">To transfer a [WorldAnchor](coordinate-systems-in-unity.md), one must establish the anchor to be transferred.</span></span> <span data-ttu-id="fa65e-118">L'utente di uno HoloLens analizza il proprio ambiente e manualmente o a livello di programmazione sceglie un punto nello spazio sia il punto di ancoraggio per condividere esperienze.</span><span class="sxs-lookup"><span data-stu-id="fa65e-118">The user of one HoloLens scans their environment and either manually or programmatically chooses a point in space to be the Anchor for the shared experience.</span></span> <span data-ttu-id="fa65e-119">I dati che rappresenta questo punto possono essere serializzati e trasmessi per gli altri dispositivi che condividono l'esperienza.</span><span class="sxs-lookup"><span data-stu-id="fa65e-119">The data that represents this point can then be serialized and transmitted to the other devices that are sharing in the experience.</span></span> <span data-ttu-id="fa65e-120">Ogni dispositivo quindi deserializza i dati di ancoraggio e prova a individuare tale punto nello spazio.</span><span class="sxs-lookup"><span data-stu-id="fa65e-120">Each device then de-serializes the anchor data and attempts to locate that point in space.</span></span> <span data-ttu-id="fa65e-121">In ordine di ancoraggio Transfer a funzionare, ogni dispositivo deve sono analizzati in un numero sufficiente di ambiente in modo che il punto rappresentato dall'ancoraggio può essere identificato.</span><span class="sxs-lookup"><span data-stu-id="fa65e-121">In order for Anchor Transfer to work, each device must have scanned in enough of the environment such that the point represented by the anchor can be identified.</span></span>

### <a name="setup"></a><span data-ttu-id="fa65e-122">Configurazione</span><span class="sxs-lookup"><span data-stu-id="fa65e-122">Setup</span></span>

<span data-ttu-id="fa65e-123">Il codice di esempio in questa pagina presenta alcuni campi che dovranno essere inizializzato:</span><span class="sxs-lookup"><span data-stu-id="fa65e-123">The sample code on this page has a few fields that will need to be initialized:</span></span>
1. <span data-ttu-id="fa65e-124">*GameObject rootGameObject* è un *GameObject* in Unity con una *WorldAnchor* componente su di esso.</span><span class="sxs-lookup"><span data-stu-id="fa65e-124">*GameObject rootGameObject* is a *GameObject* in Unity that has a *WorldAnchor* Component on it.</span></span> <span data-ttu-id="fa65e-125">Un utente di condividere esperienze si inseriranno *GameObject* ed esportare i dati ad altri utenti.</span><span class="sxs-lookup"><span data-stu-id="fa65e-125">One user in the shared experience will place this *GameObject* and export the data to the other users.</span></span>
2. <span data-ttu-id="fa65e-126">*WorldAnchor gameRootAnchor* è il *UnityEngine.XR.WSA.WorldAnchor* che si trova sul *rootGameObject*.</span><span class="sxs-lookup"><span data-stu-id="fa65e-126">*WorldAnchor gameRootAnchor* is the *UnityEngine.XR.WSA.WorldAnchor* that is on *rootGameObject*.</span></span>
3. <span data-ttu-id="fa65e-127">*Byte [] importedData* è una matrice di byte per l'ancoraggio serializzato ogni client sta ricevendo attraverso la rete.</span><span class="sxs-lookup"><span data-stu-id="fa65e-127">*byte[] importedData* is a byte array for the serialized anchor each client is receiving over the network.</span></span>

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

### <a name="exporting"></a><span data-ttu-id="fa65e-128">L'esportazione</span><span class="sxs-lookup"><span data-stu-id="fa65e-128">Exporting</span></span>

<span data-ttu-id="fa65e-129">Per esportare, è sufficiente una *WorldAnchor* e sapere che cosa verrà denominato in modo che risulti opportuno per l'app ricevente.</span><span class="sxs-lookup"><span data-stu-id="fa65e-129">To export, we just need a *WorldAnchor* and to know what we will call it such that it makes sense for the receiving app.</span></span> <span data-ttu-id="fa65e-130">Un client di condividere esperienze verrà seguire questi passaggi per esportare l'ancoraggio condiviso:</span><span class="sxs-lookup"><span data-stu-id="fa65e-130">One client in the shared experience will perform these steps to export the shared anchor:</span></span>
1. <span data-ttu-id="fa65e-131">Creare un *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="fa65e-131">Create a *WorldAnchorTransferBatch*</span></span>
2. <span data-ttu-id="fa65e-132">Aggiungere il *WorldAnchors* da trasferire</span><span class="sxs-lookup"><span data-stu-id="fa65e-132">Add the *WorldAnchors* to transfer</span></span>
3. <span data-ttu-id="fa65e-133">Avviare l'esportazione</span><span class="sxs-lookup"><span data-stu-id="fa65e-133">Begin the export</span></span>
4. <span data-ttu-id="fa65e-134">Gestire le *OnExportDataAvailable* evento sotto forma di dati diventa disponibile</span><span class="sxs-lookup"><span data-stu-id="fa65e-134">Handle the *OnExportDataAvailable* event as data becomes available</span></span>
5. <span data-ttu-id="fa65e-135">Gestire le *OnExportComplete* evento</span><span class="sxs-lookup"><span data-stu-id="fa65e-135">Handle the *OnExportComplete* event</span></span>

<span data-ttu-id="fa65e-136">Creiamo un *WorldAnchorTransferBatch* per incapsulare cosa abbiamo verrà trasferimento e quindi esportarle in byte:</span><span class="sxs-lookup"><span data-stu-id="fa65e-136">We create a *WorldAnchorTransferBatch* to encapsulate what we will be transferring and then export that into bytes:</span></span>

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

<span data-ttu-id="fa65e-137">Quando i dati diventano disponibili, inviare i byte per il client o il buffer di segmenti di dati è disponibile e trasmissione in qualsiasi modo desiderato:</span><span class="sxs-lookup"><span data-stu-id="fa65e-137">As data becomes available, send the bytes to the client or buffer as segments of data is available and send through whatever means desired:</span></span>

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

<span data-ttu-id="fa65e-138">Al termine dell'esportazione, se è stata stato trasferimento dei dati e serializzazione non è riuscita, indicare al client di rimuovere i dati.</span><span class="sxs-lookup"><span data-stu-id="fa65e-138">Once the export is complete, if we have been transferring data and serialization failed, tell the client to discard the data.</span></span> <span data-ttu-id="fa65e-139">Se la serializzazione ha avuto esito positivo, indicare al client che tutti i dati siano stati trasferiti e l'importazione è possibile avviare:</span><span class="sxs-lookup"><span data-stu-id="fa65e-139">If the serialization succeeded, tell the client that all data has been transferred and importing can start:</span></span>

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

### <a name="importing"></a><span data-ttu-id="fa65e-140">L'importazione</span><span class="sxs-lookup"><span data-stu-id="fa65e-140">Importing</span></span>

<span data-ttu-id="fa65e-141">Dopo la ricezione di tutti i byte dal mittente, sarà possibile importare i dati in un *WorldAnchorTransferBatch* e bloccare l'oggetto gioco radice nella stessa posizione fisica.</span><span class="sxs-lookup"><span data-stu-id="fa65e-141">After receiving all of the bytes from the sender, we can import the data back into a *WorldAnchorTransferBatch* and lock our root game object into the same physical location.</span></span> <span data-ttu-id="fa65e-142">Nota: importazione talvolta transiently avrà esito negativo e deve essere riprovata:</span><span class="sxs-lookup"><span data-stu-id="fa65e-142">Note: import will sometimes transiently fail and needs to be retried:</span></span>

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

<span data-ttu-id="fa65e-143">Dopo una *GameObject* è bloccato tramite il *LockObject* chiamata, avrà un *WorldAnchor* quali verrà mantenuta nella stessa posizione fisica in tutto il mondo, ma potrebbe essere in un spazio rispetto ad altri utenti delle coordinate di posizione diversa all'interno di Unity.</span><span class="sxs-lookup"><span data-stu-id="fa65e-143">After a *GameObject* is locked via the *LockObject* call, it will have a *WorldAnchor* which will keep it in the same physical position in the world, but it may be at a different location in the Unity coordinate space than other users.</span></span>


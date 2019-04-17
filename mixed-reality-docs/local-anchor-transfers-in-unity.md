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
# <a name="local-anchor-transfers-in-unity"></a>Trasferimenti di ancoraggio locale in Unity

In situazioni in cui non è possibile usare <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Anchor spaziali Azure</a>, trasferimenti di ancoraggio locale abilitare un dispositivo HoloLens esportare un ancoraggio per essere importati da un secondo dispositivo HoloLens.

>[!NOTE]
>I trasferimenti di ancoraggio locale forniscono richiamo ancoraggio meno affidabile rispetto <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Anchor spaziali Azure</a>, e dispositivi iOS e Android non sono supportati da questo approccio.

### <a name="setting-the-spatialperception-capability"></a>Impostare la funzionalità SpatialPerception

Affinché un'app di trasferire gli ancoraggi spaziali, il *SpatialPerception* deve essere attivata.

Come abilitare il *SpatialPerception* funzionalità:
1. Nell'Editor di Unity, aprire il **"Windows Media Player Settings"** riquadro (Modifica > Impostazioni di progetto > Windows Media Player)
2. Fare clic sui **"Windows Store"** scheda
3. Espandere **"Impostazioni di pubblicazione"** e selezionare il **"SpatialPerception"** funzionalità nel **"Funzionalità"** elenco

>[!NOTE]
>Se è già stato esportato il progetto di Unity a una soluzione di Visual Studio, è necessario esportare in una nuova cartella o manualmente [impostare questa funzionalità in AppxManifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

### <a name="anchor-transfer"></a>Trasferimento di ancoraggio

**Namespace:** *UnityEngine.XR.WSA.Sharing*<br>
**Tipo**: *WorldAnchorTransferBatch*

Per trasferire una [WorldAnchor](coordinate-systems-in-unity.md), uno deve essere stabilita l'ancoraggio da trasferire. L'utente di uno HoloLens analizza il proprio ambiente e manualmente o a livello di programmazione sceglie un punto nello spazio sia il punto di ancoraggio per condividere esperienze. I dati che rappresenta questo punto possono essere serializzati e trasmessi per gli altri dispositivi che condividono l'esperienza. Ogni dispositivo quindi deserializza i dati di ancoraggio e prova a individuare tale punto nello spazio. In ordine di ancoraggio Transfer a funzionare, ogni dispositivo deve sono analizzati in un numero sufficiente di ambiente in modo che il punto rappresentato dall'ancoraggio può essere identificato.

### <a name="setup"></a>Configurazione

Il codice di esempio in questa pagina presenta alcuni campi che dovranno essere inizializzato:
1. *GameObject rootGameObject* è un *GameObject* in Unity con una *WorldAnchor* componente su di esso. Un utente di condividere esperienze si inseriranno *GameObject* ed esportare i dati ad altri utenti.
2. *WorldAnchor gameRootAnchor* è il *UnityEngine.XR.WSA.WorldAnchor* che si trova sul *rootGameObject*.
3. *Byte [] importedData* è una matrice di byte per l'ancoraggio serializzato ogni client sta ricevendo attraverso la rete.

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

### <a name="exporting"></a>L'esportazione

Per esportare, è sufficiente una *WorldAnchor* e sapere che cosa verrà denominato in modo che risulti opportuno per l'app ricevente. Un client di condividere esperienze verrà seguire questi passaggi per esportare l'ancoraggio condiviso:
1. Creare un *WorldAnchorTransferBatch*
2. Aggiungere il *WorldAnchors* da trasferire
3. Avviare l'esportazione
4. Gestire le *OnExportDataAvailable* evento sotto forma di dati diventa disponibile
5. Gestire le *OnExportComplete* evento

Creiamo un *WorldAnchorTransferBatch* per incapsulare cosa abbiamo verrà trasferimento e quindi esportarle in byte:

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

Quando i dati diventano disponibili, inviare i byte per il client o il buffer di segmenti di dati è disponibile e trasmissione in qualsiasi modo desiderato:

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

Al termine dell'esportazione, se è stata stato trasferimento dei dati e serializzazione non è riuscita, indicare al client di rimuovere i dati. Se la serializzazione ha avuto esito positivo, indicare al client che tutti i dati siano stati trasferiti e l'importazione è possibile avviare:

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

### <a name="importing"></a>L'importazione

Dopo la ricezione di tutti i byte dal mittente, sarà possibile importare i dati in un *WorldAnchorTransferBatch* e bloccare l'oggetto gioco radice nella stessa posizione fisica. Nota: importazione talvolta transiently avrà esito negativo e deve essere riprovata:

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

Dopo una *GameObject* è bloccato tramite il *LockObject* chiamata, avrà un *WorldAnchor* quali verrà mantenuta nella stessa posizione fisica in tutto il mondo, ma potrebbe essere in un spazio rispetto ad altri utenti delle coordinate di posizione diversa all'interno di Unity.


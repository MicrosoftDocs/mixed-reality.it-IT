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
# <a name="local-anchor-transfers-in-unity"></a>Trasferimenti di ancoraggio locali in Unity

Nei casi in cui non è possibile usare gli <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">ancoraggi spaziali di Azure</a>, i trasferimenti di ancoraggio locali consentono a un dispositivo HoloLens di esportare un ancoraggio per l'importazione da parte di un secondo dispositivo HoloLens.

>[!NOTE]
>I trasferimenti di ancoraggio locali forniscono un richiamo di ancoraggio meno affidabile rispetto agli <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">ancoraggi spaziali di Azure</a>e i dispositivi iOS e Android non sono supportati da questo approccio.

### <a name="setting-the-spatialperception-capability"></a>Impostazione della funzionalità SpatialPerception

Per consentire a un'app di trasferire ancoraggi spaziali, è necessario abilitare la funzionalità *SpatialPerception* .

Come abilitare la funzionalità *SpatialPerception* :
1. Nell'editor di Unity aprire il riquadro **"Impostazioni lettore"** (modificare > impostazioni progetto > lettore)
2. Fare clic sulla scheda **"Windows Store"**
3. Espandere **"impostazioni di pubblicazione"** e selezionare la funzionalità **"SpatialPerception"** nell'elenco **"funzionalità"**

>[!NOTE]
>Se il progetto Unity è già stato esportato in una soluzione di Visual Studio, sarà necessario eseguire l'esportazione in una nuova cartella o [impostare manualmente questa funzionalità in appxmanifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

### <a name="anchor-transfer"></a>Trasferimento di ancoraggio

**Spazio dei nomi:** *UnityEngine. XR. WSA. sharing*<br>
**Tipo**: *WorldAnchorTransferBatch*

Per trasferire un [WorldAnchor](coordinate-systems-in-unity.md), è necessario stabilire l'ancoraggio da trasferire. L'utente di un HoloLens analizza l'ambiente e sceglie manualmente o a livello di codice un punto nello spazio come ancoraggio per l'esperienza condivisa. I dati che rappresentano questo punto possono quindi essere serializzati e trasmessi agli altri dispositivi che condividono nell'esperienza. Ogni dispositivo deserializza quindi i dati di ancoraggio e tenta di individuare il punto nello spazio. Per il corretto funzionamento del trasferimento di ancoraggio, è necessario che ogni dispositivo abbia eseguito una scansione sufficiente dell'ambiente, in modo che sia possibile identificare il punto rappresentato dall'ancoraggio.

### <a name="setup"></a>Programma di installazione

Il codice di esempio in questa pagina contiene alcuni campi che dovranno essere inizializzati:
1. *GameObject rootGameObject* è un *GameObject* in Unity in cui è presente un componente *WorldAnchor* . Un utente nell'esperienza condivisa inserisce questo *GameObject* ed Esporta i dati negli altri utenti.
2. *WorldAnchor gameRootAnchor* è *UnityEngine. XR. WSA. WorldAnchor* che si trova in *rootGameObject*.
3. *byte [] importedData* è una matrice di byte per l'ancoraggio serializzato che ogni client riceve sulla rete.

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

### <a name="exporting"></a>Esportazione

Per eseguire l'esportazione, è sufficiente un *WorldAnchor* e per sapere cosa verrà chiamato in modo da renderlo utile per l'app ricevente. Un client nell'esperienza condivisa eseguirà questa procedura per esportare l'ancoraggio condiviso:
1. Creare un *WorldAnchorTransferBatch*
2. Aggiungere il *WorldAnchors* da trasferire
3. Inizia l'esportazione
4. Gestisci l'evento *OnExportDataAvailable* quando i dati diventano disponibili
5. Gestisci evento *OnExportComplete*

Viene creato un *WorldAnchorTransferBatch* per incapsulare gli elementi che verranno trasferiti e quindi esportati in byte:

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

Quando i dati diventano disponibili, inviare i byte al client o al buffer perché i segmenti di dati sono disponibili e inviarli con qualsiasi mezzo:

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

Al termine dell'esportazione, se i dati sono stati trasferiti e la serializzazione non è riuscita, indicare al client di rimuovere i dati. Se la serializzazione ha avuto esito positivo, indicare al client che tutti i dati sono stati trasferiti e che è possibile avviare l'importazione:

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

### <a name="importing"></a>Importazione

Dopo aver ricevuto tutti i byte dal mittente, è possibile importare di nuovo i dati in un *WorldAnchorTransferBatch* e bloccare l'oggetto del gioco radice nella stessa posizione fisica. Nota: l'importazione a volte avrà esito negativo e deve essere riprovata:

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

Dopo che un *GameObject* è stato bloccato tramite la chiamata *lockobject* , avrà un *WorldAnchor* che lo manterrà nella stessa posizione fisica del mondo, ma potrebbe trovarsi in una posizione diversa nello spazio delle coordinate di Unity rispetto ad altri utenti.


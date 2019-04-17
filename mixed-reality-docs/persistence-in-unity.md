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
# <a name="persistence-in-unity"></a>Persistenza in Unity

**Namespace:** *UnityEngine.XR.WSA.Persistence*<br>
**Classe:** *WorldAnchorStore*

Il WorldAnchorStore è la chiave per la creazione di esperienze holographic dove vntana rimangono nelle posizioni reali specifico tra più istanze dell'applicazione. In questo modo gli utenti aggiungono vntana singoli o un'area di lavoro ogni volta che serve e quindi trovare in un secondo momento in cui si aspettano su molti utilizzi delle app.

## <a name="how-to-persist-holograms-across-sessions"></a>Come rendere permanente vntana tra le sessioni

Il WorldAnchorStore consentirà di rendere persistente il percorso del WorldAnchor tra le sessioni. Per rendere effettivamente persistente vntana tra le sessioni, dovrai separatamente tenere traccia del Gameobject che usano un punto di ancoraggio world particolare. È spesso opportuno creare un GameObject radice con un punto di ancoraggio del mondo e avere elementi figlio ancorati vntana dalla funzione con un offset della posizione locale.

Per caricare vntana dalle sessioni precedenti:
1. Ottenere il WorldAnchorStore
2. Caricare i dati dell'app relativi in base all'ancoraggio mondo che fornisce l'id del punto di ancoraggio il mondo
3. Caricare un ancoraggio world dal relativo id

Per salvare vntana per le sessioni future:
1. Ottenere il WorldAnchorStore
2. Salvare un ancoraggio world specificando un id
3. Salvare i dati dell'app relativi in base all'ancoraggio mondiale insieme a un id

### <a name="getting-the-worldanchorstore"></a>Introduzione di WorldAnchorStore

È consigliabile mantenere un riferimento al WorldAnchorStore intorno quindi sappiamo che siamo pronti passare quando si vuole eseguire un'operazione. Poiché si tratta di una chiamata async, potenzialmente appena start, da chiamare

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

In questo caso, StoreLoaded è il nostro gestore dopo il WorldAnchorStore ha completato il caricamento:

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

È ora disponibile un riferimento a WorldAnchorStore che verrà usato per salvare e caricare gli ancoraggi World specifico.

### <a name="saving-a-worldanchor"></a>Salvataggio di un WorldAnchor

Per salvare, è sufficiente per assegnare un nome di ciò che si sta salvando e lo associo al WorldAnchor ottenuto prima di quando si desidera salvare. Nota: tentativo di salvare gli due ancoraggi sulla stessa stringa avrà esito negativo (archivio. Salva restituirà false). È necessario eliminare il salvataggio precedente prima di salvare una nuova:

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

### <a name="loading-a-worldanchor"></a>Il caricamento di un WorldAnchor

E da caricare:

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

È inoltre possibile usare archivio. Delete () per rimuovere un ancoraggio che viene salvati in precedenza e archivio. Clear () per rimuovere tutti i dati salvati in precedenza.

### <a name="enumerating-existing-anchors"></a>L'enumerazione dei punti di ancoraggio esistente

Per individuare gli ancoraggi archiviati in precedenza, chiamare GetAllIds.

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Ologrammi persistenza per più dispositivi

È possibile usare <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Anchor spaziali Azure</a> per creare un punto di ancoraggio cloud permanenti da un WorldAnchor locale, che l'app consente quindi di individuare in più HoloLens, dispositivi iOS e Android, anche se questi dispositivi non sono presenti contemporaneamente allo stesso ora.  Poiché gli ancoraggi cloud sono persistenti, più dispositivi nel corso del tempo ogni noterà contenuto sottoposto a rendering relativo tale ancoraggio nella stessa posizione fisica.

Per iniziare a creare esperienze condivise in Unity, provare i 5 minuti <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guide introduttive di Azure spaziali Anchor Unity</a>.

Quando si è in esecuzione con Azure Anchor spaziale, è possibile quindi <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">creare e individuare gli ancoraggi in Unity</a>.

## <a name="see-also"></a>Vedere anche
* [Persistenza di ancoraggio spaziali](coordinate-systems.md#spatial-anchor-persistence)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Anchor spaziali</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Ancoraggi spaziali Azure SDK per Unity</a>

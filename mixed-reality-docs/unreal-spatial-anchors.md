---
title: Ancoraggi nello spazio in Unreal
description: Guida all'uso degli ancoraggi nello spazio in Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, ancoraggi nello spazio
ms.openlocfilehash: c35d8efc9998aac5b40de833e5acbf7f80353e6b
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840140"
---
# <a name="spatial-anchors-in-unreal"></a>Ancoraggi nello spazio in Unreal

Gli ancoraggi nello spazio consentono di salvare in modo permanente gli ologrammi nel mondo reale tra le sessioni dell'applicazione.  Questa operazione viene rilevata tramite Unreal come oggetti ARPin e viene salvata nell'archivio di ancoraggio di HoloLens per il caricamento nelle sessioni successive. 

Prima di salvare o caricare gli ancoraggi, verifica innanzitutto che l'archivio di ancoraggio sia pronto.  Il tentativo di chiamare una delle funzioni di ancoraggio di HoloLens prima che l'archivio di ancoraggio sia pronto avrà esito negativo.  

![Archivio di ancoraggi nello spazio pronto](images/unreal-spatialanchors-store-ready.PNG)

## <a name="save-anchors"></a>Salvare gli ancoraggi

Quando l'applicazione dispone di un componente che deve essere aggiunto al mondo reale, può salvarlo nell'archivio di ancoraggio con la sequenza illustrata di seguito: 

![Salvataggio degli ancoraggi nello spazio](images/unreal-spatialanchors-save.PNG)

In questo esempio, generiamo un attore in una posizione nota, creiamo un oggetto ARPin con tale posizione e un nome basato sulla classe dell'attore, aggiungiamo l'attore all'oggetto ARPin e salviamo il segnaposto nell'archivio di ancoraggio di HoloLens.  Il nome dell'ancoraggio scelto deve essere univoco, quindi in questo esempio aggiungiamo il timestamp corrente.  Se l'ancoraggio viene salvato correttamente nell'archivio di ancoraggio, può essere ispezionato nel portale del dispositivo HoloLens in System > Map manager > Anchor Files Saved On Device (Sistema > Gestore mappe > File di ancoraggio salvati sul dispositivo). 

## <a name="load-anchors"></a>Caricare gli ancoraggi

Quando un'applicazione viene avviata, puoi chiamare il progetto seguente per ripristinare i componenti nelle rispettive posizioni di ancoraggio:

![Caricamento degli ancoraggi nello spazio](images/unreal-spatialanchors-load.PNG)

In questo esempio, eseguiamo l'iterazione di tutti gli ancoraggi nell'archivio di ancoraggio, generiamo un attore in corrispondenza dell'identità e aggiungiamo tale attore all'oggetto ARPin dall'archivio di ancoraggio.  È importante generare l'attore in corrispondenza dell'identità, perché l'ancoraggio è responsabile del riposizionamento dell'ologramma nel mondo reale, in base alla posizione in cui è stato salvato; in modo che qualsiasi trasformazione aggiunta qui, aggiunga un offset all'ancoraggio. 

Eseguiamo anche una query sull'ID di ancoraggio, in modo che sia possibile generare attori diversi in base al nome salvato dell'ancoraggio. 

## <a name="remove-anchors"></a>Rimuovere gli ancoraggi 

Al termine dell'ancoraggio, puoi cancellare l'intero archivio di ancoraggio oppure rimuovere singoli ancoraggi dall'archivio di ancoraggio, in modo che non vengano inclusi nelle sessioni future: 

![Rimozione degli ancoraggi nello spazio](images/unreal-spatialanchors-remove.PNG)

## <a name="see-also"></a>Vedere anche
* [Ancoraggi nello spazio](spatial-anchors.md)
* [Sistemi di coordinate](coordinate-systems.md)

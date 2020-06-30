---
title: Ancoraggi nello spazio in Unreal
description: Guida all'uso degli ancoraggi nello spazio in Unreal
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, ancoraggi nello spazio
ms.openlocfilehash: 58394f4e27aff5070d55ed5f0d62cd81ff579d1f
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720317"
---
# <a name="spatial-anchors-in-unreal"></a>Ancoraggi nello spazio in Unreal

## <a name="overview"></a>Panoramica

Gli ancoraggi nello spazio consentono di salvare gli ologrammi nel mondo reale in più sessioni dell'applicazione.  Questi vengono esposti tramite Unreal come oggetti **ARPin** e salvati nell'archivio degli ancoraggi di HoloLens che viene caricato nelle sessioni future. 

## <a name="checking-the-anchor-store"></a>Verifica dell'archivio degli ancoraggi

Prima di salvare o caricare gli ancoraggi, verifica che l'archivio degli ancoraggi sia pronto.  Se chiami una delle funzioni di ancoraggio di HoloLens prima che l'archivio degli ancoraggi sia pronto, la chiamata avrà esito negativo.  

![Archivio di ancoraggi nello spazio pronto](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a>Salvataggio degli ancoraggi

Quando l'applicazione dispone di un componente che deve essere aggiunto al mondo reale, può salvarlo nell'archivio di ancoraggio con la sequenza illustrata di seguito: 

![Salvataggio degli ancoraggi nello spazio](images/unreal-spatialanchors-save.PNG)

Operazioni da eseguire:
1. Genera un attore in una posizione nota.
2. Crea un oggetto **ARPin** con quella posizione e un nome basato sulla classe dell'attore. 
3. Aggiungi l'attore all'oggetto **ARPin** e salva il segnaposto nell'archivio degli ancoraggi di HoloLens.  
    * Il nome dell'ancoraggio scelto deve essere univoco. In questo esempio è usato il timestamp corrente. 

4. Se l'ancoraggio viene salvato correttamente nell'archivio degli ancoraggi, puoi ispezionarlo nel portale del dispositivo HoloLens in **System > Map manager > Anchor Files Saved On Device** (Sistema > Gestore mappe > File di ancoraggio salvati sul dispositivo). 

## <a name="loading-anchors"></a>Caricamento degli ancoraggi

Quando un'applicazione viene avviata, puoi usare il progetto seguente per ripristinare i componenti nelle rispettive posizioni di ancoraggio:

![Caricamento degli ancoraggi nello spazio](images/unreal-spatialanchors-load.PNG)

Operazioni da eseguire:
1. Esegui l'iterazione di tutti gli ancoraggi nell'archivio degli ancoraggi. 
2. Genera un attore in corrispondenza dell'identità.
3. Blocca quell'attore sull'oggetto **ARPin** dall'archivio degli ancoraggi.  

    * È importante generare l'attore in corrispondenza dell'identità perché l'ancoraggio è responsabile del riposizionamento dell'ologramma nel mondo reale, in base alla posizione in cui è stato salvato. Qualsiasi trasformazione aggiunta qui aggiungerà un offset all'ancoraggio. 

Eseguiamo anche una query sull'ID di ancoraggio, in modo che sia possibile generare attori diversi in base al nome salvato dell'ancoraggio. 

## <a name="removing-anchors"></a>Rimozione degli ancoraggi 

Terminate le operazioni su un ancoraggio, puoi eliminare singoli ancoraggi o l'intero archivio degli ancoraggi con i componenti **Remove ARPin from WMRAnchor Store** (Rimuovi ARPin dall'archivio WMRAnchor) e **Remove All ARPins from WMRAnchor Store** (Rimuovi tutti gli ARPin dall'archivio WMRAnchor).

![Rimozione degli ancoraggi nello spazio](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> Tieni presente che gli ancoraggi spaziali sono ancora in versione beta, quindi visualizza di nuovo questa pagina in futuro per verificare se sono presenti informazioni e funzionalità aggiornate.

## <a name="see-also"></a>Vedere anche
* [Ancoraggi nello spazio](spatial-anchors.md)
* [Sistemi di coordinate](coordinate-systems.md)

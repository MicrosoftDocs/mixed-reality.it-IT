---
title: Visualizzazione dello stato
description: Un controllo di stato fornisce all'utente un feedback nel caso in cui sia in corso un'operazione di lunga durata.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, i controlli, dell'interfaccia utente, esperienza utente
ms.openlocfilehash: d62d86c690233f351b6c156c66eba33cb2687ea6
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813734"
---
# <a name="displaying-progress"></a>Visualizzazione dello stato

Un controllo di stato fornisce all'utente un feedback nel caso in cui sia in corso un'operazione di lunga durata. Può significare che l'utente non può interagire con l'app quando l'indicatore di stato è visibile e può anche indicare quanto è il tempo di attesa stimato, a seconda dell'indicatore usato.

![Esempio di anello lo stato di avanzamento in HoloLens](images/HoloLens2_Loader.gif)<br>
*Esempio di anello lo stato di avanzamento in HoloLens*

## <a name="types-of-progress"></a>Tipi di stato

È importante fornire informazioni su ciò che accade. Nella realtà mista agli utenti possono essere facilmente addirittura distratti dalla presenza ambiente fisico o oggetti se l'app non offre buone feedback visivo. Situazioni in cui richiedere alcuni secondi, ad esempio durante il caricamento di dati o una scena è l'aggiornamento, è consigliabile per mostrare un indicatore visivo. Sono disponibili due opzioni per mostrare all'utente che un'operazione è in corso: una **sulla barra di stato di avanzamento** o una **anello di stato**.

### <a name="progress-bar"></a>Indicatore di stato

![Esempio di barra di stato di avanzamento in HoloLens](images/640px-progressbar.jpg)

Un indicatore di stato Mostra la percentuale di completamento di un'attività. Deve essere usato durante un'operazione la cui durata è noto (indicatore), ma lo stato di avanzamento non deve bloccare l'interazione dell'utente con l'app.

### <a name="progress-ring"></a>Anello di stato

![Esempio di anello lo stato di avanzamento in HoloLens](images/640px-progressring.jpg)

Solo un anello di stato ha uno stato indeterminato e deve essere usato quando qualsiasi ulteriore interazione dell'utente viene bloccata fino al completamento dell'operazione.

### <a name="progress-with-a-custom-object"></a>Stato di avanzamento con un oggetto personalizzato

![Stato di avanzamento con esempio di trama personalizzati in HoloLens](images/640px-progresscustom.jpg)

È possibile aggiungere all'app personalità e all'identità del marchio personalizzando il controllo di stato di avanzamento con oggetti 2D e 3D personalizzati.

## <a name="best-practices"></a>Procedure consigliate
* Uno stretto accoppiamento [del billboard o tag-along](billboarding-and-tag-along.md) per la visualizzazione dello stato di avanzamento poiché l'utente può facilmente spostare propria testa in uno spazio vuoto e perdere contesto. L'app potrebbe sembrare che è arrestato in modo anomalo se l'utente non riesce a visualizzare i risultati. Billboarding e tag-along è incorporata nel prefab lo stato di avanzamento.
* È sempre consigliabile fornire informazioni sullo stato relative all'utente ciò che accade. Il prefab lo stato di avanzamento fornisce diversi stili tra cui lo stato di ring-tipo standard di Windows per fornire lo stato. È anche possibile usare una rete mesh di personalizzati con un'animazione se si desidera che lo stile di avanzamento in modo da allinearsi al marchio dell'app.

## <a name="see-also"></a>Vedere anche
* [Gli script di stato di avanzamento e prefabs nel Toolkit di realtà mista](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [Rettangolo di selezione](app-bar-and-bounding-box.md)
* [Oggetto che supporta interazioni](interactable-object.md)
* [Raccolta di oggetti](object-collection.md)
* [Billboarding e tag-along](billboarding-and-tag-along.md)

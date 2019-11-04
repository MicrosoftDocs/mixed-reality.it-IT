---
title: Visualizzazione dello stato di avanzamento
description: Un controllo di stato fornisce all'utente un feedback nel caso in cui sia in corso un'operazione di lunga durata.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, controlli, interfaccia utente, UX
ms.openlocfilehash: 43b4802e7c821c98c847509ace950f381da12f95
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437533"
---
# <a name="displaying-progress"></a>Visualizzazione dello stato di avanzamento

<br>

<img src="images/HoloLens2_Loader.gif" alt="Progress ring example in HoloLens" width="940px">

Un controllo di stato fornisce all'utente un feedback nel caso in cui sia in corso un'operazione di lunga durata. Può significare che l'utente non può interagire con l'app quando l'indicatore di stato è visibile e può anche indicare quanto è il tempo di attesa stimato, a seconda dell'indicatore usato.

<br>

---

## <a name="types-of-progress"></a>Tipi di stato

È importante fornire le informazioni sull'utente su ciò che accade. In realtà mista gli utenti possono essere facilmente distratti da ambienti fisici o oggetti se l'app non fornisce un feedback visivo efficace. Per le situazioni in cui sono necessari alcuni secondi, ad esempio quando i dati vengono caricati o una scena viene aggiornata, è consigliabile visualizzare un indicatore visivo. Sono disponibili due opzioni per indicare all'utente che è in corso un'operazione, ovvero un indicatore di **stato** o un **anello di avanzamento**.

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a>Barra di stato<br>
        Un indicatore di stato Mostra la percentuale di completamento di un'attività. Deve essere usato durante un'operazione la cui durata è nota (determinata), ma lo stato di avanzamento non deve bloccare l'interazione dell'utente con l'app.<br>
        <br>
        *Image: esempio di indicatore di stato in HoloLens*
    :::column-end:::
        :::column:::
        spazio ![](images/spacer-20x582.png)<br>
       esempio ![indicatore di stato in HoloLens](images/640px-progressbar.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a>Anello di stato<br>
        Un anello di avanzamento ha solo uno stato indeterminato e deve essere usato quando ogni ulteriore interazione con l'utente viene bloccata fino al completamento dell'operazione.<br>
        <br>
        *Immagine: esempio di anello di stato in HoloLens*
    :::column-end:::
        :::column:::
        spazio ![](images/spacer-20x582.png)<br>
       esempio di ![dell'anello di stato in HoloLens](images/640px-progressring.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a>Stato di avanzamento con un oggetto personalizzato<br>
        È possibile aggiungere la personalità e l'identità del marchio dell'app personalizzando il controllo dello stato di avanzamento con oggetti 2D/3D personalizzati.<br>
        <br>
        *Immagine: esempio di avanzamento con mesh personalizzato in HoloLens*
    :::column-end:::
        :::column:::
        spazio ![](images/spacer-20x582.png)<br>
       esempio di ![stato con mesh personalizzato in HoloLens](images/640px-progresscustom.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a>Procedure consigliate
* È strettamente correlato alla visualizzazione dello stato di avanzamento [, in quanto](billboarding-and-tag-along.md) l'utente può facilmente spostarne l'intestazione in uno spazio vuoto e perdere il contesto. È possibile che l'app si trovi in modo anomalo se l'utente non è in grado di visualizzare alcun elemento. Il tabellone e i tag-along sono incorporati nella prefabbrica di avanzamento.
* È sempre opportuno fornire informazioni sullo stato relative a ciò che accade all'utente. Il prefabbricato di avanzamento fornisce vari stili visivi, tra cui lo stato di avanzamento del tipo di anello standard di Windows. È anche possibile usare una mesh personalizzata con un'animazione se si vuole che lo stile dello stato di avanzamento sia allineato al marchio dell'app.

<br>

---

## <a name="see-also"></a>Vedi anche
* [Script di avanzamento e prefabbricati sul Toolkit di realtà mista](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [Rettangolo di delimitazione](app-bar-and-bounding-box.md)
* [Oggetto che supporta interazioni](interactable-object.md)
* [Raccolta di oggetti](object-collection.md)
* [Billboarding e tag-along](billboarding-and-tag-along.md)

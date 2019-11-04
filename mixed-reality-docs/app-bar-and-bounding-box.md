---
title: Rettangolo di delimitazione e barra dell'app
description: La barra dell'app è un menu a livello di oggetto contenente una serie di pulsanti visualizzati sul bordo inferiore dei limiti di un ologramma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Realtà mista di Windows, barra dell'app, rettangolo di delimitazione
ms.openlocfilehash: f09187bc2a3969a8f844711052e15433f5449d6d
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437061"
---
# <a name="bounding-box-and-app-bar"></a>Rettangolo di delimitazione e barra dell'app
![Il delimitatore è l'interfaccia standard per la manipolazione di oggetti in realtà mista.](images/640px-boundingbox-hero.jpg)<br>

<br>

---

## <a name="what-is-the-bounding-box"></a>Che cos'è il rettangolo di delimitazione?

Il delimitatore è l'interfaccia standard per la manipolazione di oggetti in realtà mista. Fornisce all'utente la convenienza che l'oggetto è attualmente modificabile. In HoloLens 2 il rettangolo di delimitazione funziona con la manipolazione diretta della mano e risponde alla vicinanza finger's dell'utente. Mostra commenti visivi per aiutare l'utente a percepire la distanza dall'oggetto.

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a>Ridimensionamento di un oggetto<br>
        Gli angoli del rettangolo di delimitazione indicano all'utente che l'oggetto può essere ridimensionato. Gli handle seguono un modello molto noto per la regolazione della scala. Questa offerta visiva mostra agli utenti l'area totale dell'oggetto, anche se non è visibile al di fuori di una modalità di regolazione. Questo è particolarmente importante perché, in caso contrario, un oggetto bloccato a un altro oggetto o a una superficie può sembrare comportarsi come se fosse presente spazio che non dovrebbe essere presente.<br>
        <br>
        *Ciclo video: ridimensionamento di un oggetto tramite il rettangolo di delimitazione*
    :::column-end:::
        :::column:::
        spazio ![](images/spacer-20x582.png)<br>
       ![punto di visualizzazione HoloLens di ridimensionamento di un oggetto tramite il rettangolo di delimitazione](images/HoloLens2_BoundingBox.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a>Rotazione di un oggetto<br>
        Il affordances rettangolare verticale sui bordi del rettangolo di delimitazione sono indicatori di rotazione. In questo modo l'utente garantisce una maggiore regolazione degli ologrammi posizionati. Non solo è possibile modificare e ridimensionare, ma ora ruotare anche.<br>
        <br>
        *Ciclo video: rotazione di un oggetto tramite il rettangolo di delimitazione*
    :::column-end:::
        :::column:::
        spazio ![](images/spacer-20x582.png)<br>
       ![punto di visualizzazione HoloLens della rotazione di un oggetto tramite il rettangolo di delimitazione](images/HoloLens2_BoundingBox_Rotate.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a>Feedback visivo sulle prossimità della mano su HoloLens 2<br>
        In HoloLens 2 è presente un segnale visivo aggiuntivo che può aiutare la percezione dell'utente della profondità. Un anello vicino alla loro parte viene visualizzato e ridimensionato quando il dito si avvicina all'oggetto. L'anello alla fine converge in un punto quando viene raggiunto lo stato premuto. Questa convenienza visiva consente all'utente di comprendere la distanza dall'oggetto.<br>
        <br>
        *Ciclo video: esempio di feedback visivo basato sulla prossimità a un rettangolo di delimitazione*
    :::column-end:::
        :::column:::
        spazio ![](images/spacer-20x582.png)<br>
       ![commenti e suggerimenti visivi sulla prossimità della mano](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::

<br>

**Per lo sviluppo di app Unity, vedere [il riquadro delimitatore in Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**

<br>

---

## <a name="what-is-the-app-bar"></a>Che cos'è la barra dell'app?

La barra dell'app è un menu a livello di oggetto contenente una serie di pulsanti visualizzati sul bordo inferiore dei limiti di un ologramma. Questo modello viene in genere usato per offrire agli utenti la possibilità di rimuovere e modificare gli ologrammi. La barra dell'app è stata progettata principalmente per gestire gli oggetti posizionati nell'ambiente di un utente. Insieme al rettangolo di delimitazione, un utente ha il controllo completo sulla posizione e sulla modalità di orientamento degli oggetti in realtà mista.

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a>La barra dell'app segue l'utente<br>
        Poiché questo modello viene usato con oggetti bloccati dal mondo, quando un utente si sposta intorno all'oggetto, la barra dell'app verrà sempre visualizzata sul lato degli oggetti più vicino all'utente. Sebbene questo non sia il tabellone, ottiene lo stesso risultato. impedire la posizione di un utente per occludere o bloccare la funzionalità che altrimenti sarebbe disponibile da una posizione diversa nell'ambiente. <br>
        <br>
        *Ciclo video: aggirare un ologramma, la barra dell'app segue*
    :::column-end:::
        :::column:::
        spazio ![](images/spacer-20x582.png)<br>
       ![aggirare un ologramma. Segue la barra dell'app.](images/HoloLens2_AppBarFollowing.gif)<br>
    :::column-end:::
:::row-end:::

<br>



**Per lo sviluppo di app Unity, vedere [barra delle app in Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)**

<br>

---

## <a name="see-also"></a>Vedi anche
* [Oggetto che supporta interazioni](interactable-object.md)
* [Testo in Unity](text-in-unity.md)
* [Raccolta di oggetti](object-collection.md)
* [Visualizzazione dello stato](progress.md)

---
title: Rettangolo di delimitazione e barra dell'app
description: La barra dell'app è un menu a livello di oggetto contenente una serie di pulsanti visualizzati sul bordo inferiore dei limiti di un ologramma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Realtà mista di Windows, barra dell'app, rettangolo di delimitazione
ms.openlocfilehash: d289be31129324c6ff419b69dbce52bd8f62eb64
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829680"
---
# <a name="bounding-box-and-app-bar"></a>Rettangolo di delimitazione e barra dell'app
![Il delimitatore è l'interfaccia standard per la manipolazione di oggetti in realtà mista.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a>Che cos'è il rettangolo di delimitazione?

Il delimitatore è l'interfaccia standard per la manipolazione di oggetti in realtà mista. Fornisce all'utente la convenienza che l'oggetto è attualmente modificabile. Gli angoli indicano all'utente che l'oggetto può anche essere ridimensionato. Questa offerta visiva mostra agli utenti l'area totale dell'oggetto, anche se non è visibile al di fuori di una modalità di regolazione. Questo è particolarmente importante perché, in caso contrario, un oggetto bloccato a un altro oggetto o a una superficie può sembrare comportarsi come se fosse presente spazio che non dovrebbe essere presente. In HoloLens 2 il rettangolo di delimitazione funziona con la manipolazione diretta della mano e risponde alla vicinanza finger's dell'utente. Mostra commenti visivi per aiutare l'utente a percepire la distanza dall'oggetto. 

![HoloLens punto di vista della scalabilità di un oggetto tramite il rettangolo di delimitazione](images/HoloLens2_BoundingBox.gif)<br>
*Ridimensionamento di un oggetto tramite il rettangolo di delimitazione*

Gli handle negli angoli del rettangolo di delimitazione seguono un modello molto noto per la regolazione della scala. 

![HoloLens punto di visualizzazione della rotazione di un oggetto tramite il rettangolo di delimitazione](images/HoloLens2_BoundingBox_Rotate.gif)<br>
*Rotazione di un oggetto tramite il rettangolo di delimitazione*


![Feedback visivo sulla prossimità della mano](images/HoloLens2_Proximity.gif)<br>
*Feedback visivo basato sulla prossimità*

Il affordances rettangolare verticale sui bordi del rettangolo di delimitazione sono indicatori di rotazione. In questo modo l'utente garantisce una maggiore regolazione degli ologrammi posizionati. Non solo è possibile modificare e ridimensionare, ma ora ruotare anche.

* Per lo sviluppo di app Unity, vedere rettangolo [di delimitazione nel Toolkit di realtà mista-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)



## <a name="what-is-the-app-bar"></a>Che cos'è la barra dell'app?

La barra dell'app è un menu a livello di oggetto contenente una serie di pulsanti visualizzati sul bordo inferiore dei limiti di un ologramma. Questo modello viene in genere usato per offrire agli utenti la possibilità di rimuovere e modificare gli ologrammi.

Poiché questo modello viene usato con oggetti bloccati dal mondo, quando un utente si sposta intorno all'oggetto, la barra dell'app verrà sempre visualizzata sul lato degli oggetti più vicino all'utente. Sebbene questo non sia il tabellone, ottiene lo stesso risultato. impedire la posizione di un utente per occludere o bloccare la funzionalità che altrimenti sarebbe disponibile da una posizione diversa nell'ambiente.

![Aggirare un ologramma. Segue la barra dell'app.](images/HoloLens2_AppBarFollowing.gif)<br>
*Aggirare un ologramma, la barra dell'app segue*

La barra dell'app è stata progettata principalmente per gestire gli oggetti posizionati nell'ambiente di un utente. Insieme al rettangolo di delimitazione, un utente ha il controllo completo sulla posizione e sulla modalità di orientamento degli oggetti in realtà mista.

* Per lo sviluppo di app Unity, vedere [barra delle applicazioni nel Toolkit di realtà mista-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)

## <a name="see-also"></a>Vedere anche
* [Oggetto che supporta interazioni](interactable-object.md)
* [Testo in Unity](text-in-unity.md)
* [Raccolta di oggetti](object-collection.md)
* [Visualizzazione dello stato](progress.md)

---
title: Finestra di contenimento e barra dell'App
description: Barra dell'App è un menu a livello di oggetto che contiene una serie di pulsanti che viene visualizzato sul bordo inferiore dei limiti di ologramma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Realtà mista di Windows, App a barre, rettangolo di selezione
ms.openlocfilehash: d289be31129324c6ff419b69dbce52bd8f62eb64
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829680"
---
# <a name="bounding-box-and-app-bar"></a>Finestra di contenimento e barra dell'App
![Rettangolo di selezione è l'interfaccia standard per la manipolazione dell'oggetto nella realtà mista.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a>Che cos'è la finestra di contenimento?

Rettangolo di selezione è l'interfaccia standard per la manipolazione dell'oggetto nella realtà mista. L'utente fornisce un intuitività che l'oggetto è attualmente modificabile. Gli angoli informare l'utente che l'oggetto è possibile scalare anche. Questo intuitività visual Mostra agli utenti l'area totale dell'oggetto, anche se non è visibile all'esterno di una modalità di regolazione. Ciò è particolarmente importante poiché se non esiste, potrebbe apparire un oggetto a un altro oggetto o nell'area ancorato si comporti come se si è verificato lo spazio intorno a esso che non deve essere presenti. In 2 HoloLens, il rettangolo di selezione funziona con la manipolazione diretta mano e risponde alla prossimità del dito dell'utente. Mostra commenti visivi per consentire all'utente di percepire la distanza dall'oggetto. 

![HoloLens punto di vista del ridimensionamento di un oggetto tramite rettangolo di selezione](images/HoloLens2_BoundingBox.gif)<br>
*Il ridimensionamento di un oggetto tramite rettangolo di selezione*

Gli handle negli angoli del rettangolo seguono un modello ampiamente riconosciuto per regolare la scala. 

![HoloLens punto di vista della rotazione di un oggetto tramite rettangolo di selezione](images/HoloLens2_BoundingBox_Rotate.gif)<br>
*Ruotare un oggetto tramite rettangolo di selezione*


![Indicazioni visive in prossimità di mano](images/HoloLens2_Proximity.gif)<br>
*Feedback visivo in base alla prossimità*

I affordance rettangolare verticale sui bordi del rettangolo di selezione sono indicatori di rotazione. Questo account offre all'utente ulteriori regolazione loro vntana inserito. Non solo può è regolare e scalabilità, ma ora ruotare anche.

* Per lo sviluppo di app Unity, vedere [rettangolo di selezione in Unity-Toolkit realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)



## <a name="what-is-the-app-bar"></a>Che cos'è barra dell'App?

Barra dell'App è un menu a livello di oggetto che contiene una serie di pulsanti che viene visualizzato sul bordo inferiore dei limiti di ologramma. Questo modello viene comunemente usato per concedere agli utenti la possibilità di rimuovere e modificare vntana.

Poiché questo modello viene usato con gli oggetti che sono world bloccato, come un utente si sposta l'oggetto barra dell'App viene sempre visualizzato sul lato degli oggetti più vicino all'utente. Anche se ciò non è del billboard, in modo efficace raggiunge lo stesso risultato. impedisce la funzionalità di blocco che altrimenti sarebbero disponibile da una posizione diversa nel proprio ambiente o posizione per nasconde i colori di un utente.

![Walking intorno ologramma. Segue barra dell'App.](images/HoloLens2_AppBarFollowing.gif)<br>
*Walking intorno ologramma, segue barra dell'App*

Barra dell'App è stata progettata principalmente come un modo per gestire gli oggetti inseriti in un ambiente dell'utente. Usato in combinazione con il rettangolo di selezione, un utente dispone del controllo completo su come e dove gli oggetti sono orientati in realtà mista.

* Per lo sviluppo di app Unity, vedere [barra dell'App in Unity-Toolkit realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)

## <a name="see-also"></a>Vedere anche
* [Oggetto che supporta interazioni](interactable-object.md)
* [Testo in Unity](text-in-unity.md)
* [Raccolta di oggetti](object-collection.md)
* [Visualizzazione dello stato](progress.md)

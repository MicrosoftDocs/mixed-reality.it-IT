---
title: Oggetto si
description: Un pulsante già da tempo, una metafora utilizzata per l'attivazione di un evento in tutto il mondo astratto 2D. Nel mondo tridimensionale realtà mista, non dobbiamo riguardare esclusivamente questo mondo di astrazione più.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Realtà mista, controlli, interazione, dell'interfaccia utente, esperienza utente
ms.openlocfilehash: f349d21707375690e00b0f7e465634c62be1537e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601182"
---
# <a name="interactable-object"></a>Oggetto si

Un pulsante già da tempo, una metafora utilizzata per l'attivazione di un evento in tutto il mondo astratto 2D. Nel mondo tridimensionale realtà mista, non dobbiamo riguardare esclusivamente questo mondo di astrazione più. Qualsiasi elemento può essere un' **oggetto si** che attiva un evento. Un oggetto si può essere rappresentato come un elemento da una tazza di caffè sulla tabella in un fumetto mobile in modalità wireless. È comunque effettuare uso dei pulsanti tradizionali in alcune situazioni, ad esempio in finestra di dialogo dell'interfaccia utente. La rappresentazione visiva del pulsante dipende dal contesto.

![Immagine banner interactible oggetto](images/640px-interactibleobject-hero-640px.jpg)


Nel  **[Toolkit di realtà mista](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, abbiamo creato una serie di script di Unity e prefabs che consenta di creare oggetti si. È possibile usare questi per creare qualsiasi tipo di oggetto che l'utente può interagire con, tramite questi stati interazione standard: osservazione, destinazione e premuto. È possibile personalizzare la progettazione visiva facilmente con le proprie risorse. Le animazioni dettagliate possono essere personalizzate creando e assegnando i clip di animazione corrispondenti per gli stati di interazione nel controller di animazione di Unity o utilizzo di offset e scalabilità. 


## <a name="visual-feedback-for-the-different-input-interaction-states"></a>Indicazioni visive per gli stati di interazione di input diversi

In realtà mista, poiché gli oggetti holographic vengono combinati con l'ambiente reale, potrebbe essere difficile comprendere quali oggetti sono si. Per gli oggetti si durante l'utilizzo, è importante fornire un feedback visivo differenziato per ogni stato di input. Ciò consente all'utente di capire quale parte della tua esperienza è si e lo rende la certezza con metodo di interazione tra coerente.

Per tutti gli oggetti che l'utente può interagire con, è consigliabile avere diverse indicazioni visive per questi tre stati di input:
* **Osservazione**: Stato di inattività predefinito dell'oggetto.
* **Destinazione**: L'oggetto di destinazione con il cursore sguardo, finger puntatore prossimità o movimento del controller.
* **Premuto**: Quando viene premuto l'oggetto con indice puntato movimento, premere un dito o pulsante di selezione del controller di movimento.

![Pulsante holographic](images/640px-interactibleobject-holographicbutton-650px.jpg)<br>
*Osservazione dello stato, lo stato di destinazione e lo stato di premuto*

Nella realtà mista di Windows, è possibile trovare gli esempi dei diversi stati di input nel menu Start e pulsanti della barra di App la visualizzazione. È possibile usare tecniche quali l'evidenziazione o la scalabilità per fornire indicazioni visive agli stati di input dell'utente.

HoloLens 2, poiché supporta mano completamente articolati e rilevamento di input, possiamo fornire affordance aggiuntive in base alla prossimità in messi a disposizione. Il [pulsante in 2 HoloLens](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) illustrato in questo esempio.

![Pulsante pressable](images/640px-interactibleobject-pressablebutton-650px.jpg)<br>




## <a name="interactable-object-samples"></a>Esempi di oggetti si

### <a name="mesh-button"></a>Pulsante mesh

![Pulsante mesh](images/640px-interactibleobject-meshbutton.jpg)

Questi sono esempi che usano le primitive e maglie 3D importati come oggetti si. È possibile assegnare facilmente diversi valori di scala, offset e il colore per rispondere a ogni stato di interazione di input.

### <a name="toolbar"></a>Barra degli strumenti

![Barra degli strumenti](images/640px-interactibleobject-toolbar.jpg)

Una barra degli strumenti è un modello diffuso nelle esperienze di realtà mista. È ad esempio un semplice insieme di pulsanti con altri comportamenti [Billboarding e tag-along](billboarding-and-tag-along.md). Questo esempio usa uno script Billboarding e tag-along dal MixedRealityToolkit. È possibile controllare comportamenti dettagliati inclusi distanza, spostare i valori di velocità e la soglia.

### <a name="traditional-button"></a>Pulsante tradizionale

![Pulsante tradizionale](images/640px-interactibleobject-traditionalbutton.jpg)

Questo esempio mostra un pulsante Stile tradizionale 2D. Ogni stato di input ha una profondità leggermente diverso e una proprietà di animazione.

### <a name="other-examples"></a>Altri esempi

![Pulsante di comando](images/640px-interactibleobject-pushbutton.jpg)<br>
*Pulsante di comando*
<br>
![Oggetto vita reale](images/640px-interactibleobject-reallifeobject.jpg)<br>
*Oggetto di uno scenario reale*

Con HoloLens, è possibile sfruttare lo spazio fisico. Si immagini un pulsante di comando holographic su una parete fisico. O che ne dici una tazza di caffè su una tabella reale? Uso di modelli 3D importati dalla modellazione del software, è possibile creare un oggetto si che è simile a oggetti di uno scenario reale. Poiché si tratta di un oggetto digitale, possiamo aggiungere interazioni magico scrivendo a esso.

## <a name="interactable-object-in-mixed-reality-toolkit"></a>Oggetto si nel Toolkit di realtà mista
È possibile trovare il [esempi di Interactable dell'oggetto nel Toolkit di realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)


## <a name="see-also"></a>Vedere anche
* [Pulsante pressable sul Toolkit di realtà mista-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [Raccolta di oggetti](object-collection.md)
* [Del billboard e tag-along](billboarding-and-tag-along.md)

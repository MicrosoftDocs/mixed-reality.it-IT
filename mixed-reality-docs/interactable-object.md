---
title: Oggetto interagibile
description: Un pulsante è a lungo una metafora usata per attivare un evento nel mondo astratto 2D. Nel mondo della realtà mista tridimensionale, non dobbiamo più limitarci a questo mondo dell'astrazione.
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Realtà mista, controlli, interazione, interfaccia utente, UX
ms.openlocfilehash: 57299cbb758a69603fc68ad5d43af8f2216e5104
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415356"
---
# <a name="interactable-object"></a>Oggetto interagibile

Un pulsante è a lungo una metafora usata per attivare un evento nel mondo astratto 2D. Nel mondo della realtà mista tridimensionale, non dobbiamo più limitarci a questo mondo dell'astrazione. Qualsiasi elemento può essere un **oggetto interagibile** che attiva un evento. Un oggetto interactabile può essere rappresentato da qualsiasi elemento da un caffè della tabella a un pallone in aria. Si usano ancora i pulsanti tradizionali in determinate situazioni, ad esempio nell'interfaccia utente della finestra di dialogo. La rappresentazione visiva del pulsante dipende dal contesto.

![Oggetti Interactible](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a>Proprietà importanti dell'oggetto interagibile

### <a name="visual-cue"></a>Segnale visivo

I segnali visivi sono segnali sensoriali ricevuti dall'occhio sotto forma di luce ed elaborati dal sistema visuale durante la percezione visiva. Poiché il sistema visivo è dominante in molte specie, in particolare gli esseri umani, i segnali visivi rappresentano una grande fonte di informazioni in merito alla percezione del mondo.

In realtà mista, poiché gli oggetti olografici sono combinati con l'ambiente reale, potrebbe essere difficile comprendere quali oggetti possono interagire. Per tutti gli oggetti interagibili nell'esperienza, è importante fornire un segnale visivo differenziato per ogni stato di input. Ciò consente all'utente di comprendere quale parte dell'esperienza è interactabile e rende l'utente affidabile con un metodo di interazione coerente.

#### <a name="far-interactions"></a>Interazioni a distanza

Per tutti gli oggetti che gli utenti possono interagire con lo sguardo, il raggio di mano e il raggio del controller di movimento, è consigliabile avere un segnale visivo diverso per questi tre stati di input:
* **Impostazione predefinita (osservazione)** : Stato inattivo predefinito dell'oggetto.
* **Targeted (hover)** : Quando l'oggetto è destinato a un cursore a sguardi, a una prossimità del dito o al puntatore del controller di movimento.
* **Selezionato**: Quando l'oggetto viene premuto con il gesto dell'aria, premere il pulsante di selezione o il controller di movimento.

È possibile usare tecniche come l'evidenziazione o il ridimensionamento per fornire un segnale visivo agli Stati di input dell'utente. In realtà mista di Windows, è possibile trovare gli esempi di visualizzazione di diversi Stati di input nel menu Start e nei pulsanti della barra delle applicazioni. 

![Esempio di visualizzazione dello stato di osservazione, dello stato di destinazione e dello stato premuto](images/640px-interactibleobject-states.png)<br>
*Esempio di visualizzazione dello stato di osservazione, dello stato di destinazione e dello stato premuto*

![Stato di osservazione, stato di destinazione e stato premuto sul pulsante olografico](images/MRTK_InteractableState.png)<br>
*Stato di osservazione, stato di destinazione e stato premuto sul pulsante olografico*

#### <a name="neardirect-interactions"></a>Interazioni near (Direct)

HoloLens 2 supporta l'input di rilevamento a mano articolato che consente di interagire con gli oggetti. Senza feedback tattile e percezione di profondità perfetta, a volte può essere difficile indicare la distanza di mano da un oggetto o se si sta toccando. È importante fornire segnali visivi sufficienti per comunicare lo stato dell'oggetto e, in particolare, le mani in relazione agli ologrammi.

Usare il feedback visivo per comunicare quanto segue:
* **Impostazione predefinita (osservazione)** : Stato inattivo predefinito dell'oggetto.
* **Passaggio del mouse**: Quando la mano si avvicina a un ologramma, modificare gli oggetti visivi per comunicare che la mano è destinata a ologrammi. 
* **Distanza e punto di interazione**: Man mano che si avvicina l'ologramma, progettare il feedback per comunicare il punto di interazione proiettato, nonché la distanza dall'oggetto del dito
* **Inizio contatto**: Modificare gli oggetti visivi (chiaro, colore) per comunicare che si è verificato il tocco
* **Colto**: Modificare gli oggetti visivi (chiaro, colore) quando l'oggetto viene afferrato.
* **Fine contatto**: Modifica gli oggetti visivi (chiaro, colore) quando il tocco è terminato.

![Esempio di visualizzazione degli Stati near Interaction](images/640px-interactibleobject-states-near.jpg)<br>
*Esempio di visualizzazione degli Stati near Interaction*

Il [pulsante in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) Mostra l'esempio di visualizzazione di diversi Stati di interazione di input.

![Esempio di pulsante stampabile in HoloLens 2](images/640px-interactibleobject-pressablebutton-650px2.jpg)<br>
*Esempio di pulsante stampabile in HoloLens 2*

In HoloLens 2 è presente un segnale visivo aggiuntivo che migliora la confidenza dell'utente sulla percezione della profondità. L'anello sulla punta viene visualizzato e viene ridimensionato quando il dito si avvicina all'oggetto. Il Ring converge infine in un punto in stato di pressione. Questa convenienza visiva consente all'utente di comprendere la distanza dall'oggetto.

![Visualizzazione dell'anello della punta](images/640px-interactibleobject-pressablebutton-650px3.jpg)<br>
*Visualizzazione dell'anello a mano in HoloLens 2*

![Feedback visivo sulla prossimità della mano](images/HoloLens2_Proximity.gif)<br>
*Esempio di feedback visivo basato sul riquadro di prossimità*


### <a name="audio-cue"></a>Cue audio
Per le interazioni dirette, il feedback audio appropriato può migliorare notevolmente l'esperienza utente. Usare il feedback audio per comunicare quanto segue:
* **Inizio contatto**: Riprodurre un suono all'avvio del tocco
* **Fine contatto**: Riproduci suono al termine del tocco
* **Inizio della cattura**: Riproduci suono all'avvio della pinza
* **Fine della pinza**: Riprodurre un suono al termine della cattura

### <a name="voice-command"></a>Comando Voice
Per tutti gli oggetti interagibili, è importante supportare opzioni di interazione alternative. Per impostazione predefinita, è consigliabile supportare il comando Voice per tutti gli oggetti che possono interagire. Per migliorare l'individuabilità, è possibile fornire la descrizione comando sullo stato del passaggio del mouse.

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="Descrizione comando per il comando Voice" width="350"><br/>*Descrizione comando per il comando Voice*

## <a name="sizing"></a>Ridimensionamento
Per garantire che tutti gli oggetti interagibili possano essere facilmente modificati dagli utenti, si consiglia di assicurarsi che l'interoperabilità soddisfi le dimensioni minime (l'angolo visivo spesso misurato in gradi di arco visivo) in base alla distanza in base alla quale viene posizionata dall'utente. L'angolo visivo è basato sulla distanza tra gli occhi dell'utente e l'oggetto e rimane costante, mentre la dimensione fisica della destinazione può variare a seconda della distanza tra le modifiche apportate dall'utente. Per determinare le dimensioni fisiche necessarie di un oggetto in base alla distanza dall'utente, provare a usare un calcolo dell'angolo visivo come [questo](http://elvers.us/perception/visualAngle/).

Di seguito sono riportati i consigli per le dimensioni minime del contenuto interactabile.

### <a name="target-size-for-direct-hand-interaction"></a>Dimensioni di destinazione per l'interazione diretta con la mano
| distanza | Angolo di visualizzazione | Size |
|---------|---------|---------|
| 45cm  | non inferiore a 2 ° | 1,6 x 1,6 cm |

![Dimensioni di destinazione per l'interazione diretta con la mano](images/TargetSizingNear.jpg)<br>
*Dimensioni di destinazione per l'interazione diretta con la mano*

Quando si creano i pulsanti per l'interazione diretta, si consiglia una dimensione minima maggiore di 3,2 x 3,2 cm per assicurarsi che lo spazio disponibile sia sufficiente per contenere un'icona e potenzialmente un testo * *

| distanza | Dimensione minima |
|---------|---------|
| 45cm  | 3,2 x 3,2 cm |

![Dimensioni di destinazione per i pulsanti](images/TargetSizingButtons.png)<br>
*Dimensioni di destinazione per i pulsanti*


### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>Dimensioni di destinazione per l'interazione con raggio o sguardo
| distanza | Angolo di visualizzazione | Size |
|---------|---------|---------|
| 2m  | non minore di 1 ° | 3,5 x 3,5 cm |

![Dimensioni di destinazione per l'interazione con raggio o sguardo](images/TargetSizingFar.jpg)<br>
*Dimensioni di destinazione per l'interazione con raggio o sguardo*

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a>Creazione di un oggetto interagibile con il Toolkit di realtà mista (MRTK)

Nel Toolkit per la **[realtà mista](https://github.com/Microsoft/MixedRealityToolkit-Unity)** è possibile trovare la serie di script Unity e prefabbricati che consentiranno di creare oggetti interagibili. È possibile usarli per fare in modo che gli oggetti rispondano a diversi tipi di Stati di interazione di input.

* [Con cui](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [Pulsante](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [Scena degli esempi di interazione della mano](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

Lo shader standard di MixedRealityToolkit offre diverse opzioni, ad esempio la **luce vicina** , che consente di creare suggerimenti visivi e audio.
* [Shader standard MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


## <a name="see-also"></a>Vedere anche

* [Rettangolo di delimitazione](app-bar-and-bounding-box.md)
* [Raccolta di oggetti](object-collection.md)
* [Billboarding e tag-along](billboarding-and-tag-along.md)
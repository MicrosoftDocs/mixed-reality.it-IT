---
title: Oggetto interagibile
description: Un pulsante è a lungo una metafora usata per attivare un evento nel mondo astratto 2D. Nel mondo della realtà mista tridimensionale, non dobbiamo più limitarci a questo mondo dell'astrazione.
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Realtà mista, controlli, interazione, interfaccia utente, UX
ms.openlocfilehash: 87979d2d7b7de4a384b42b5059239e9b830a92e8
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723230"
---
# <a name="interactable-object"></a>Oggetto interagibile

![Oggetti Interactible](images/UX/UX_Hero_Interactable.jpg)

Un pulsante è a lungo una metafora usata per attivare un evento nel mondo astratto 2D. Nel mondo della realtà mista tridimensionale, non dobbiamo più limitarci a questo mondo dell'astrazione. Qualsiasi elemento può essere un **oggetto interagibile** che attiva un evento. Un oggetto interactabile può essere rappresentato da qualsiasi elemento da un caffè della tabella a un pallone in aria. Si usano ancora i pulsanti tradizionali in determinate situazioni, ad esempio nell'interfaccia utente della finestra di dialogo. La rappresentazione visiva del pulsante dipende dal contesto.

<br>

---


## <a name="important-properties-of-the-interactable-object"></a>Proprietà importanti dell'oggetto interagibile

### <a name="visual-cues"></a>Segnali visivi

I segnali visivi sono segnali sensoriali ricevuti dall'occhio sotto forma di luce ed elaborati dal sistema visuale durante la percezione visiva. Poiché il sistema visivo è dominante in molte specie, in particolare gli esseri umani, i segnali visivi rappresentano una grande fonte di informazioni in merito alla percezione del mondo.

Poiché gli oggetti olografici vengono combinati con l'ambiente reale in realtà mista, potrebbe essere difficile comprendere quali oggetti è possibile interagire. Per tutti gli oggetti interagibili nell'esperienza, è importante fornire segnali visivi differenziati per ogni stato di input. Ciò consente all'utente di comprendere quale parte dell'esperienza è interactabile e rende l'utente affidabile usando un metodo di interazione coerente.

<br>

---

### <a name="far-interactions"></a>Interazioni a distanza

Per tutti gli oggetti che gli utenti possono interagire con lo sguardo, il raggio di mano e il raggio del controller di movimento, è consigliabile avere un segnale visivo diverso per questi tre stati di input:

:::row:::
    :::column:::
       ![interactibleobject-States-default](images/interactibleobject-states-default.jpg)<br>
       **Stato predefinito (osservazione)**<br>
        Stato inattivo predefinito dell'oggetto.
    Il cursore non si trova nell'oggetto. La mano non è stata rilevata.
    :::column-end:::
    :::column:::
       ![](images/interactibleobject-states-targeted.jpg) di destinazione di interactibleobject<br>
        **Stato di destinazione (hover)**<br>
        Quando l'oggetto è destinato a un cursore a sguardi, a una prossimità del dito o al puntatore del controller di movimento.
    Il cursore si trova sull'oggetto. La mano è stata rilevata, pronta.
    :::column-end:::
    :::column:::
       ![interactibleobject-stati-premuti](images/interactibleobject-states-pressed.jpg)<br>
       **Stato premuto**<br>
        Quando l'oggetto viene premuto con un movimento di tocco aereo, premere il pulsante Seleziona del controller di movimento o del dito.
    Il cursore si trova sull'oggetto. Viene rilevata una mano, aria toccata.
    :::column-end:::
:::row-end:::

<br>

---

È possibile usare tecniche come l'evidenziazione o il ridimensionamento per fornire segnali visivi per lo stato di input dell'utente. In realtà mista, è possibile trovare gli esempi di visualizzazione di diversi Stati di input nel menu Start e con i pulsanti della barra delle applicazioni. 

Ecco come appaiono questi stati in un **pulsante olografico**:

:::row:::
    :::column:::
       ![interactibleobject-States-default](images/MRTK_InteractableState-default.jpg)<br>
       **Stato predefinito (osservazione)**<br>
    :::column-end:::
    :::column:::
       ![](images/MRTK_InteractableState-targeted.jpg) di destinazione di interactibleobject<br>
        **Stato di destinazione (hover)**<br>
    :::column-end:::
    :::column:::
       ![interactibleobject-stati-premuti](images/MRTK_InteractableState-pressed.jpg)<br>
       **Stato premuto**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a>Near Interactions (Direct) 

HoloLens 2 supporta l'input di rilevamento a mano articolato che consente di interagire con gli oggetti. Senza commenti e suggerimenti tattili e una profonda percezione della profondità, a volte può essere difficile capire quanto è lontana la mano da un oggetto o se lo si sta toccando. È importante fornire segnali visivi sufficienti per comunicare lo stato dell'oggetto e in particolare lo stato delle mani in relazione a tale oggetto.

Usare il feedback visivo per comunicare quanto segue:
* **Impostazione predefinita (osservazione)** : stato inattivo predefinito dell'oggetto.
* **Hover**: quando una mano si avvicina a un ologramma, modificare gli oggetti visivi per comunicare che la mano è destinata a ologrammi. 
* **Distanza e punto di interazione**: poiché la mano si avvicina a un ologramma, progettare il feedback per comunicare il punto di interazione proiettato, oltre a quanto lontano dall'oggetto il dito
* **Inizio contatto**: modificare gli oggetti visivi (chiaro, colore) per comunicare che si è verificato un tocco
* **Colto**: modificare gli oggetti visivi (chiaro, colore) quando l'oggetto viene afferrato
* **Estremità del contatto**: modificare gli oggetti visivi (chiaro, colore) al termine del tocco

<br>

---

:::row:::
    :::column:::
        ![passaggio del mouse (lontano)](images/640px-interactibleobject-states-near-hover.jpg)<br>
        **Passaggio del mouse (lontano)**<br>
        Evidenziazione basata sulla prossimità del manuale.
    :::column-end:::
    :::column:::
        ![hover (near)](images/640px-interactibleobject-states-near-hovernear.jpg)<br>
        **Passaggio del mouse (vicino)**<br>
        Evidenziare le modifiche delle dimensioni in base alla distanza della mano.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![toccare/premere](images/640px-interactibleobject-states-near-press.jpg)<br>
        **Tocco/pressione**<br>
        Commenti visivi e audio.
    :::column-end:::
    :::column:::
        ![afferrare](images/640px-interactibleobject-states-near-grasp.jpg)<br>
        **Comprendere**<br>
        Commenti visivi e audio.
    :::column-end:::
:::row-end:::

<br>

<br>

---

Un [pulsante in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) è un esempio di visualizzazione dei diversi Stati di interazione di input:

:::row:::
    :::column:::
        ![Impostazione predefinita](images/640px-interactibleobject-pressablebutton-default.jpg)<br>
        **Impostazione predefinita**<br>
    :::column-end:::
    :::column:::
        ![](images/640px-interactibleobject-pressablebutton-hover.jpg) hover<br>
        **Passare il mouse**<br>
        Rivelare un effetto di illuminazione basato su prossimità.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Tocco](images/640px-interactibleobject-pressablebutton-touch.jpg)<br>
        **Tocco**<br>
        Mostra effetto Ripple.
    :::column-end:::
    :::column:::
        ![Premere](images/640px-interactibleobject-pressablebutton-press.jpg)<br>
        **Premere**<br>
        Spostare il pannello anteriore.
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a>Il segnale visivo "Ring" su HoloLens 2<br>
        In HoloLens 2 è presente un segnale visivo aggiuntivo che può aiutare la percezione dell'utente della profondità. Un anello vicino alla loro parte viene visualizzato e ridimensionato quando il dito si avvicina all'oggetto. L'anello alla fine converge in un punto quando viene raggiunto lo stato premuto. Questa convenienza visiva consente all'utente di comprendere la distanza dall'oggetto.<br>
        <br>
        *Ciclo video: esempio di feedback visivo basato sulla prossimità a un rettangolo di delimitazione*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![commenti e suggerimenti visivi sulla prossimità della mano](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a>Segnali audio

Per le interazioni dirette, il feedback audio appropriato può migliorare notevolmente l'esperienza utente. Usare il feedback audio per comunicare quanto segue:
* **Inizio contatto**: riprodurre un suono quando inizia il tocco
* **Terminazione contatto**: riprodurre un suono al termine del tocco
* **Inizio**avvio: riprodurre un suono quando viene avviata la cattura
* **Estremità**di chiusura: riprodurre un suono quando termina la cattura

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a>Esecuzione di comandi vocali<br>
        Per tutti gli oggetti interagibili, è importante supportare opzioni di interazione alternative. Per impostazione predefinita, è consigliabile che i [comandi vocali](voice-design.md) siano supportati per gli oggetti che possono interagire. Per migliorare l'individuabilità, è anche possibile fornire una descrizione comando durante lo stato del passaggio del mouse.<br>
        <br>
        *Image: descrizione comando per il comando Voice*
    :::column-end:::
        :::column:::
       ![comando vocale](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a>Consigli sul ridimensionamento 

Per garantire che tutti gli oggetti interagibili possano essere facilmente modificati dagli utenti, si consiglia di assicurarsi che l'interoperabilità soddisfi le dimensioni minime (l'angolo visivo spesso misurato in gradi di arco visivo) in base alla distanza in base alla quale viene posizionata dall'utente. L'angolo visivo è basato sulla distanza tra gli occhi dell'utente e l'oggetto e rimane costante, mentre la dimensione fisica della destinazione può variare a seconda della distanza tra le modifiche apportate dall'utente. Per determinare le dimensioni fisiche necessarie di un oggetto in base alla distanza dall'utente, provare a usare un calcolo dell'angolo visivo come [questo](https://elvers.us/perception/visualAngle/).

Di seguito sono riportati i consigli per le dimensioni minime del contenuto interactabile.


### <a name="target-size-for-direct-hand-interaction"></a>Dimensioni di destinazione per l'interazione diretta con la mano

| Distanza | Angolo di visualizzazione | Dimensioni |
|---------|---------|---------|
| 45cm  | non inferiore a 2 ° | 1,6 x 1,6 cm |

dimensioni di destinazione ![per l'interazione diretta con la mano](images/TargetSizingNear.jpg)<br>
*Dimensioni di destinazione per l'interazione diretta con la mano*

<br>

### <a name="target-size-for-buttons"></a>Dimensioni di destinazione per i pulsanti

Quando si creano i pulsanti per l'interazione diretta, si consiglia una dimensione minima maggiore di 3,2 x 3,2 cm per assicurarsi che lo spazio disponibile sia sufficiente per contenere un'icona e potenzialmente un testo.

| Distanza | Dimensione minima |
|---------|---------|
| 45cm  | 3,2 x 3,2 cm |

dimensioni di destinazione ![per i pulsanti](images/TargetSizingButtons.png)<br>
*Dimensioni di destinazione per i pulsanti*

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>Dimensioni di destinazione per l'interazione con raggio o sguardo
| Distanza | Angolo di visualizzazione | Dimensioni |
|---------|---------|---------|
| 2m  | non minore di 1 ° | 3,5 x 3,5 cm |

![dimensioni di destinazione per l'interazione con raggio o sguardo](images/TargetSizingFar.jpg)<br>
*Dimensioni di destinazione per l'interazione con raggio o sguardo*


<br>

---


## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a>Oggetto interactabile in MRTK (Mixed Reality Toolkit) per Unity

In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** è possibile usare lo script [**interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) per fare in modo che gli oggetti rispondano a diversi tipi di Stati di interazione di input. Supporta vari tipi di temi che consentono di definire gli Stati di visualizzazione controllando le proprietà dell'oggetto, ad esempio colore, dimensioni, materiale e shader.

* [Con cui](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [Scena degli esempi di interazione della mano](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

Lo shader standard di MixedRealityToolkit offre diverse opzioni, ad esempio la **luce vicina** , che consente di creare suggerimenti visivi e audio.
* [Shader standard MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a>Vedi anche

* [Cursori](cursors.md)
* [Raggio della mano](point-and-commit.md)
* [Button](button.md)
* [Oggetto che supporta interazioni](interactable-object.md)
* [Rettangolo di selezione e barra dell'app](app-bar-and-bounding-box.md)
* [Manipolazione](direct-manipulation.md)
* [Menu a mano](hand-menu.md)
* [Menu adiacente](near-menu.md)
* [Raccolta di oggetti](object-collection.md)
* [Comando vocale](voice-input.md)
* [Tastiera](keyboard.md)
* [Descrizione comando](tooltip.md)
* [Slate](slate.md)
* [Dispositivo di scorrimento](slider.md)
* [Shader](shader.md)
* [Billboarding e tag-along](billboarding-and-tag-along.md)
* [Visualizzazione dello stato](progress.md)
* [Magnetismo di superficie](surface-magnetism.md)

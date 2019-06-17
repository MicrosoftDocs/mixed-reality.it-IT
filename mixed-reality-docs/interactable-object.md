---
title: Oggetto si
description: Un pulsante già da tempo, una metafora utilizzata per l'attivazione di un evento in tutto il mondo astratto 2D. Nel mondo tridimensionale realtà mista, non dobbiamo riguardare esclusivamente questo mondo di astrazione più.
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Realtà mista, controlli, interazione, dell'interfaccia utente, esperienza utente
ms.openlocfilehash: b0397e00763f70e4caf55a84b6541085e56fafd4
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148757"
---
# <a name="interactable-object"></a>Oggetto si

Un pulsante già da tempo, una metafora utilizzata per l'attivazione di un evento in tutto il mondo astratto 2D. Nel mondo tridimensionale realtà mista, non dobbiamo riguardare esclusivamente questo mondo di astrazione più. Qualsiasi elemento può essere un' **oggetto si** che attiva un evento. Un oggetto si può essere rappresentato come un elemento da una tazza di caffè sulla tabella in un fumetto mobile in modalità wireless. È comunque effettuare uso dei pulsanti tradizionali in alcune situazioni, ad esempio in finestra di dialogo dell'interfaccia utente. La rappresentazione visiva del pulsante dipende dal contesto.

![Oggetti interactible](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a>Importanti proprietà dell'oggetto si

### <a name="visual-cue"></a>Indicazione visiva

Segnali visivi sono sensoriali suggerimenti ricevuti dall'occhio del lettore sotto forma di luce ed elaborati dal sistema di visual percezione visiva. Perché il sistema visual dominante specie molti, in particolare gli esseri umani, segnali visivi sono grandi fonti di informazioni nel modo in cui viene percepito del mondo.

In realtà mista, poiché gli oggetti holographic vengono combinati con l'ambiente reale, potrebbe essere difficile comprendere quali oggetti sono si. Per gli oggetti si durante l'utilizzo, è importante fornire indizio visivo differenziata per ogni stato di input. Ciò consente all'utente di capire quale parte della tua esperienza è si e lo rende la certezza con metodo di interazione tra coerente.

#### <a name="far-interactions"></a>Interazioni estrema

Per tutti gli oggetti che l'utente può interagire con sguardo, ray mano e il raggio del controller di movimento, è consigliabile avere diversi visivo per questi tre stati di input:
* **Predefinito (osservazione)** : Stato di inattività predefinito dell'oggetto.
* **Destinazione (al passaggio del mouse)** : L'oggetto di destinazione con il cursore sguardo, finger puntatore prossimità o movimento del controller.
* **Premuto**: Quando viene premuto l'oggetto con indice puntato movimento, premere un dito o pulsante di selezione del controller di movimento.

È possibile usare tecniche quali l'evidenziazione o la scalabilità per fornire un indizio visivo agli stati di input dell'utente. Nella realtà mista di Windows, è possibile trovare gli esempi dei diversi stati di input nel menu Start e pulsanti della barra di App la visualizzazione. 

![Esempio di visualizzazione dello stato di osservazione, lo stato di destinazione e lo stato di premuto](images/640px-interactibleobject-states.png)<br>
*Esempio di visualizzazione dello stato di osservazione, lo stato di destinazione e lo stato di premuto*

![Lo stato di osservazione, lo stato di destinazione e premuto di stato nel pulsante holographic](images/MRTK_InteractableState.png)<br>
*Lo stato di osservazione, lo stato di destinazione e premuto di stato nel pulsante holographic*

#### <a name="neardirect-interactions"></a>Interazioni NEAR(Direct)

HoloLens 2 supporta mano articolati e input che è possibile interagire con gli oggetti di rilevamento. Senza feedback aptico e perfetto percezione di profondità in alcuni casi può essere difficile capire la modalità a portata di mano la mano da un oggetto, o se sono tocca. È importante offrire sufficiente segnali visivi per comunicare lo stato dell'oggetto e, in particolare della disposizione in relazione al vntana.

Usare un feedback visivo per comunicare la seguente:
* **Predefinito (osservazione)** : Stato di inattività predefinito dell'oggetto.
* **Passare il mouse**: Quando mano è quasi ologramma, oggetti visivi di modifica per comunicare tale disponibilità è destinato a ologramma. 
* **Distanza e punto di interazione**: Come si avvicina a mano ologrammi, progettare commenti e suggerimenti per comunicare il punto di interazione, anche proiettato come tutt'altro che l'oggetto è il dito
* **Contattare Begin**: Oggetti visivi di modifica (luce, colore) per comunicare un tocco si è verificata
* **Compreso**: Modificare gli oggetti visivi (luce, colore) quando l'oggetto è compreso.
* **Contattare End**: Modificare gli oggetti visivi (luce, colore) quando è terminato il tocco.

![Esempio di visualizzazione vicino gli stati di interazione](images/640px-interactibleobject-states-near.jpg)<br>
*Esempio di visualizzazione vicino gli stati di interazione*

Il [pulsante in 2 HoloLens](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) Mostra l'esempio di interazione di input diversi stati di visualizzazione.

![Esempio di pulsante pressable HoloLens 2](images/640px-interactibleobject-pressablebutton-650px2.jpg)<br>
*Esempio di pulsante pressable HoloLens 2*

2 HoloLens, prevede un segnale visivo aggiuntivo che consente di migliorare la fiducia dell'utente sulla percezione profondità. L'anello nella punta del dito viene visualizzato e vengono ridimensionate verso il basso con la punta del dito avvicini all'oggetto. L'anello converge alla fine di un punto sullo stato di pressione. Questo intuitività visual consente all'utente di comprendere la distanza dall'oggetto.

![Visualizzazione di anello punta del dito](images/640px-interactibleobject-pressablebutton-650px3.jpg)<br>
*Visualizzazione di anello punta del dito 2 HoloLens*

![Indicazioni visive in prossimità di mano](images/HoloLens2_Proximity.gif)<br>
*Esempio di risposta visiva in base alla prossimità - finestra di delimitazione*


### <a name="audio-cue"></a>Segnale audio
Per le interazioni dirette mano, feedback audio corretto Puoi migliorare notevolmente l'esperienza dell'utente. Usare audio commenti e suggerimenti per comunicare la seguente:
* **Iniziare a contatto**: Riproduci un suono quando inizia il tocco
* **Fine contatto**: Riprodurre un suono sull'estremità di tocco
* **Quadratini di ridimensionamento begin**: Riproduci un suono quando viene avviato quadratini di ridimensionamento
* **Scarica end**: Riprodurre un suono sull'estremità di quadratini di ridimensionamento

### <a name="voice-command"></a>Comandi vocali
Per tutti gli oggetti si, è importante supportare opzioni di interazione alternativo. Parola chiave default, è consigliabile per supportare i comandi vocali per tutti gli oggetti si. Per migliorare l'individuabilità, è possibile fornire una descrizione comando sullo stato al passaggio del mouse.

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="Descrizione comando per i comandi vocali" width="350"><br/>*Descrizione comando per i comandi vocali*

## <a name="sizing"></a>Ridimensionamento
Per garantire che tutti gli oggetti si possono facilmente essere modificate da utenti è consigliabile garantire la si soddisfa una dimensione minima, spesso espressa in gradi angolo visual, in base alla distanza che viene inserito dall'utente. Gradi angolo visual è basato sulla distanza tra l'utente e l'oggetto e rimane costante, mentre le dimensioni fisiche della destinazione potrebbero cambiare quando la distanza dalle modifiche utente. Per determinare la dimensione fisica necessaria di un oggetto in base alla distanza da un che e dal grado angolo visual provare a utilizzare una calcolatrice, ad esempio: http://elvers.us/perception/visualAngle/

Di seguito sono le raccomandazioni per le dimensioni minime del contenuto si

### <a name="target-size-for-direct-hand-interaction"></a>Dimensioni di destinazione per l'interazione diretta mano
| distanza | Angolo di visualizzazione | Dimensione |
|---------|---------|---------|
| 45cm  | non inferiore a 2° | 1.6 a 1,6 cm |

![Dimensioni di destinazione per l'interazione diretta mano](images/TargetSizingNear.jpg)<br>
*Dimensioni di destinazione per l'interazione diretta mano*

Quando si creano i pulsanti per l'interazione diretta, si consiglia una dimensione minima maggiore di cm 3.2 x 3.2 per garantire che vi sia spazio sufficiente per contenere un'icona e potenzialmente alcune testo * *

| distanza | Dimensione minima |
|---------|---------|
| 45cm  | 3.2 x 3.2 cm |

![Dimensioni di destinazione per i pulsanti](images/TargetSizingButtons.png)<br>
*Dimensioni di destinazione per i pulsanti*


### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>Dimensioni di ray mano di destinazione o estasiati interazione
| distanza | Angolo di visualizzazione | Dimensione |
|---------|---------|---------|
| 2 minuti  | non inferiore a 1° | 3.5 3,5 cm |

![Dimensioni di ray mano di destinazione o estasiati interazione](images/TargetSizingFar.jpg)<br>
*Dimensioni di ray mano di destinazione o estasiati interazione*

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a>Creazione oggetto si con Toolkit di realtà mista (MRTK)

Nel  **[Toolkit di realtà mista](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , è possibile trovare la serie di script Unity e prefabs che consenta di creare oggetti si. È possibile usare questi a rendere gli oggetti di rispondere ai vari tipi di stati di interazione di input.

* [Si](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [Pulsante](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [Mano interazione esempi scena](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

Shader Standard del MixedRealityToolkit fornisce diverse opzioni, ad esempio **light prossimità** che consente di creare segnali audio e video.
* [MRTK Shader Standard](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


## <a name="see-also"></a>Vedere anche

* [rettangolo di selezione](app-bar-and-bounding-box.md)
* [Raccolta di oggetti](object-collection.md)
* [Billboarding e tag-along](billboarding-and-tag-along.md)
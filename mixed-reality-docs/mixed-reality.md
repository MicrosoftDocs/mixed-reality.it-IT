---
title: Ce cos'è la realtà mista?
description: Questo articolo definisce la realtà mista e illustra la posizione occupata dai dispositivi AR e VR semplici e dai dispositivi Windows Mixed Reality, come Microsoft HoloLens e i visori VR immersive Windows Mixed Reality, nello spettro della realtà mista.
author: brandonbray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: realtà mista, olografico, ar, vr, mr, xr, realtà aumentata, realtà virtuale, spiegazione
ms.localizationpriority: high
ms.openlocfilehash: 541752ef32149f64f9b85616883c284b33bb8fed
ms.sourcegitcommit: 8daefb763d1f23fe02b95b766b00b373f04c5c2d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2020
ms.locfileid: "86447907"
---
# <a name="what-is-mixed-reality"></a>Ce cos'è la realtà mista?

![Puntamento e commit con le mani in HoloLens 2](images/02_MixedRealitySlashMixedReality.png)

La realtà mista è il risultato della fusione del mondo fisico con il mondo digitale. È l'evoluzione successiva nell'interazione tra uomo, computer e ambiente e rende possibili cose che finora si limitavano all'immaginazione. È stata resa possibile grazie ai progressi nei settori della visione artificiale, dell'elaborazione grafica, della tecnologia di visualizzazione e dei sistemi di input. Il termine *realtà mista* è stato originariamente introdotto in un documento del 1994 a cura di Paul Milgram e Fumio Kishino, "[A Taxonomy of Mixed Reality Visual Displays](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)" (Tassonomia dei dispositivi di visualizzazione nella realtà mista). Il documento ha introdotto il concetto di *continuum di virtualizzazione* e ha illustrato come si applica ai dispositivi di visualizzazione la categorizzazione della tassonomia. Da quel momento in poi l'applicazione della realtà mista è andata oltre i dispositivi di visualizzazione per estendersi anche all'input ambientale, all'audio spaziale e alla posizione.

![Spettro della realtà mista](images/mixedrealityspectrum-worlds.png)<br>
*Immagine: la realtà mista è il risultato della fusione del mondo fisico con il mondo digitale.*

<br>

---

## <a name="environmental-input-and-perception"></a>Input e percezione ambientali

Negli ultimi decenni è stata approfondita la relazione tra input umano e del computer. Esiste anche una disciplina ampiamente studiata nota come *interazione uomo-computer* o HCI. L'input umano avviene attraverso un'ampia gamma di mezzi, tra cui tastiere, mouse, tocco, input penna, voce e anche il tracciamento dello scheletro tramite Kinect.

I miglioramenti apportati ai sensori e all'elaborazione stanno dando vita a una nuova area di input computer dagli ambienti. L'interazione tra computer e ambienti è essenzialmente una conoscenza o *percezione* ambientale. Da qui derivano i nomi delle API di Windows che rivelano informazioni ambientali e che sono indicate come [API di percezione](https://docs.microsoft.com/uwp/api/Windows.Perception). L'input ambientale acquisisce elementi come la posizione di una persona nell'ambiente (ad esempio il [tracciamento del movimento della testa](coordinate-systems.md)), le superfici e i confini (ad esempio il [mapping spaziale](spatial-mapping.md) e la [conoscenza della scena](scene-understanding.md)), l'illuminazione ambientale, l'audio ambientale, il riconoscimento degli oggetti e la posizione.

<br>

![Diagramma di Venn che mostra le interazioni tra computer, persone e ambienti](images/mixed-reality-venn-diagram-300px.png)<br> 
*Immagine: interazioni tra computer, persone e ambienti.*

<br>

A questo punto, la combinazione di tutti e tre gli elementi, **elaborazione del computer, input umano e input ambientale**, consente di creare vere esperienze di realtà mista. Il movimento nel mondo fisico può tradursi in movimento nel mondo digitale. I confini nel mondo fisico possono influenzare le esperienze delle applicazioni, ad esempio le esperienze di gioco, nel mondo digitale. Senza l'input ambientale, non è possibile fondere le esperienze tra realtà fisiche e digitali.<br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a>Spettro della realtà mista

Dal momento che la realtà mista è una combinazione dei mondi fisico e digitale, queste due realtà definiscono i poli estremi di uno spettro noto come continuum di virtualizzazione, per semplicità indicato come *spettro della realtà mista*. Sul lato sinistro è presente la realtà fisica in cui si trova l'uomo e sul lato destro è presente la realtà digitale corrispondente.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>Realtà aumentata e realtà virtuale

La maggior parte dei telefoni cellulari attualmente presenti sul mercato non dispone di alcuna capacità di conoscenza ambientale. Le esperienze offerte pertanto non possono combinare realtà fisiche e digitali. Le esperienze di sovrapposizione di grafica sui flussi video del mondo fisico costituiscono la *realtà aumentata*. Le esperienze che occludono la vista per presentare un'esperienza digitale costituiscono la *realtà virtuale*. Come puoi osservare, le esperienze consentite tra questi due estremi costituiscono la *realtà mista*:
* Iniziando dal mondo fisico, inserisci un oggetto digitale, ad esempio un ologramma, come se fosse effettivamente presente.
* Partendo dal mondo fisico, una rappresentazione digitale di un'altra persona, un avatar, mostra la posizione in cui si trovava quando ha lasciato gli appunti. In altre parole, queste sono esperienze che rappresentano la collaborazione asincrona in momenti diversi.
* Partendo da un mondo digitale, i confini fisici del mondo fisico, ad esempio i muri e i mobili, vengono visualizzati digitalmente all'interno dell'esperienza per aiutare gli utenti a evitare gli oggetti fisici.


<br>

![Spettro della realtà mista](images/mixedrealityspectrum.png)<br>
*Immagine: spettro della realtà mista*

<br>

La maggior parte delle offerte di realtà aumentata e realtà virtuale attualmente disponibili rappresenta una parte molto piccola di questo spettro. Costituiscono tuttavia sottoinsiemi del più ampio spettro della realtà mista. Windows 10 è stato creato tenendo conto dell'intero spettro e consente di combinare rappresentazioni digitali di persone, luoghi e cose con il mondo reale.




## <a name="devices-and-experiences"></a>Dispositivi ed esperienze


Esistono due tipi principali di dispositivi che offrono esperienze Windows Mixed Reality:
1. **Dispositivi olografici.** Sono caratterizzati dalla capacità del dispositivo di collocare contenuti digitali nel mondo reale come se vi si trovassero realmente.
2. **Dispositivi immersive.** Sono caratterizzati dalla capacità del dispositivo di creare un senso di "presenza", nascondendo il mondo fisico e sostituendolo con un'esperienza digitale.

<table>
<tr>
<th width="30%"> Caratteristica</th><th width="35%"> Dispositivi olografici</th><th width="35%"> Dispositivi immersive</th>
</tr><tr>
<td><strong>Dispositivo di esempio</strong></td><td> Microsoft HoloLens<br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> Samsung HMD Odyssey+<br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><strong>Display</strong></td><td> Display trasparente. Consente all'utente di vedere l'ambiente fisico mentre indossa il visore VR.</td><td> Display opaco. Blocca la vista dell'ambiente fisico mentre si indossa il visore VR.</td>
</tr><tr>
<td><strong>Movimento</strong></td><td> Movimento di sei gradi di libertà, con rotazione e traslazione.</td><td> Movimento di sei gradi di libertà, con rotazione e traslazione.</td>
</tr>
</table>



Tieni presente che il fatto che un dispositivo sia connesso a un PC separato (tramite cavo USB o Wi-Fi) o con tethering o che sia un dispositivo autonomo (senza tethering), non indica se si tratta di un dispositivo olografico o immersive. Certamente, le funzionalità che migliorano la mobilità determinano una migliore esperienza e i dispositivi olografici e immersive possono essere sia con che senza tethering.


Il progresso tecnologico ha reso possibile esperienze di realtà mista. Non sono disponibili al momento dispositivi in grado di offrire esperienze che coprono l'intero spettro. Windows 10 tuttavia offre una piattaforma di realtà mista comune per produttori e sviluppatori di dispositivi. I dispositivi odierni possono supportare una gamma specifica nell'ambito dello spettro della realtà mista. Nel tempo nuovi dispositivi espanderanno tale gamma. In futuro i dispositivi olografici diventeranno più immersive e i dispositivi immersive diventeranno più olografici.

<br>

![Tipi di dispositivi nello spettro della realtà mista](images/Final_WhatIsMixedReality07.png)<br>
*Immagine: posizione occupata dai dispositivi nello spettro della realtà mista*

È spesso preferibile pensare al tipo di esperienza che uno sviluppatore di applicazioni o giochi vuole creare. Le esperienze in genere indicano un punto o una parte specifica dello spettro. Gli sviluppatori devono quindi valutare le capacità dei dispositivi a cui mirare. Ad esempio, le esperienze che si basano sul mondo fisico verranno eseguite in modo ottimale in HoloLens.
* **Verso sinistra (in prossimità della realtà fisica).** Gli utenti rimangono presenti nell'ambiente fisico e non hanno mai l'impressione di aver lasciato tale ambiente.
* **Al centro (completamente nella realtà mista).** Queste esperienze fondono il mondo reale e il mondo digitale. Chi ha visto il film [Jumanji](https://en.wikipedia.org/wiki/Jumanji) può riconciliare il modo in cui la struttura fisica della casa in cui si è svolta la trama è stata fusa con una giungla.
* **Verso destra (in prossimità della realtà digitale).** Gli utenti sperimentano un ambiente completamente digitale e non sono consapevoli di ciò che accade nell'ambiente fisico che li circonda.


## <a name="see-also"></a>Vedere anche

* [Che cos'è un ologramma?](hologram.md)
* [Comprendere i concetti di base della realtà mista](get-started-with-mr.md#understand-the-basics)
* [Iniziare a progettare e a creare prototipi](design.md)
* [Informazioni sugli strumenti e sull'architettura](development.md)


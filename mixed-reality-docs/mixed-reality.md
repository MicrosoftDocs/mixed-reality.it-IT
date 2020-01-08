---
title: Ce cos'è la realtà mista?
description: Questo articolo definisce la realtà mista e illustra i dispositivi AR e VR semplici, nonché i dispositivi di realtà mista di Windows, come Microsoft HoloLens e gli auricolari a realtà mista di Windows, che siedono lungo lo spettro della realtà mista.
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: realtà mista, olografica, AR, VR, Mr, XR, realtà aumentata, realtà virtuale, spiegazione
ms.openlocfilehash: e3205590ce46e0fc9113421e0dbaeb87fe6bc0c2
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334029"
---
# <a name="what-is-mixed-reality"></a>Ce cos'è la realtà mista?

![Puntare ed eseguire il commit con hands on HoloLens 2](images/02_MixedRealitySlashMixedReality.png)

La realtà mista è il risultato della fusione del mondo fisico con il mondo digitale. È l'evoluzione successiva nell'interazione tra uomo, computer e ambiente e rende possibili cose che finora si limitavano all'immaginazione. Questo è possibile grazie a miglioramenti in visione artificiale, potenza di elaborazione grafica, tecnologia di visualizzazione e sistemi di input. Il termine *realtà mista* è stato originariamente introdotto in un documento 1994 di Paul Milgram e Fumio Kishino, "[una tassonomia di visualizzazioni visive realtà miste](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)". Nel documento è stato introdotto il concetto di *continuità della virtualizzazione*e si è concentrato sul modo in cui viene applicata la categorizzazione della tassonomia. Da allora, l'applicazione della realtà mista va oltre le visualizzazioni. Include anche l'input ambientale, il suono spaziale e la posizione.

![lo spettro di realtà misto](images/mixedrealityspectrum-worlds.png)<br>
*Immagine: la realtà mista è il risultato della fusione del mondo fisico con Digiworld.*

<br>

---

## <a name="environmental-input-and-perception"></a>Input e percezione ambientali

Negli ultimi decenni è stata esplorata la relazione tra l'input umano e il computer. Ha anche una disciplina ampiamente studiata nota come *interazione tra computer umani* o HCI. L'input umano si verifica attraverso un'ampia gamma di mezzi, tra cui tastiere, topi, tocco, input penna, voce e anche rilevamento scheletrico Kinect.

I progressi nei sensori e nell'elaborazione sono la crescita di una nuova area di input del computer dagli ambienti. L'interazione tra computer e ambienti è in effetti la comprensione o la *percezione*ambientale. Di conseguenza, i nomi delle API in Windows che rivelano informazioni ambientali sono detti [API percettive](https://docs.microsoft.com/uwp/api/Windows.Perception). L'input ambientale acquisisce elementi come la posizione di una persona nel mondo, ad esempio il [rilevamento della testa](coordinate-systems.md), le superfici e i limiti, ad esempio il [mapping spaziale](spatial-mapping.md) e la [comprensione della scena](scene-understanding.md), l'illuminazione ambientale, il suono ambientale, il riconoscimento degli oggetti e la posizione.

<br>

![diagramma Venn che mostra le interazioni tra computer, persone e ambienti](images/mixed-reality-venn-diagram-300px.png)<br>*immagine  
: le interazioni tra computer, persone e ambienti.*

<br>

A questo punto, la combinazione di tutti e tre i**computer di elaborazione, input umano e input ambientale**: consente di creare esperienze reali miste. Lo spostamento attraverso il mondo fisico può tradursi in movimento nel mondo digitale. I limiti nel mondo fisico possono influenzare le esperienze delle applicazioni, ad esempio giochi, nel mondo digitale. Senza input ambientale, le esperienze non possono essere combinate tra le realtà fisiche e digitali.<br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a>Spettro della realtà mista

Dal momento che la realtà mista unisce i mondi fisici e digitali, queste due realtà definiscono le estremità polari di uno spettro noto come continuità della virtualizzazione. Per semplicità, si fa riferimento a questo come lo *spettro della realtà mista*. Sul lato sinistro è presente la realtà fisica in cui si trovano gli utenti, sul lato destro è disponibile la realtà digitale corrispondente.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>Realtà aumentata rispetto alla realtà virtuale

Attualmente la maggior parte dei telefoni cellulari sul mercato non ha alcuna capacità di comprensione ambientale. In questo modo, le esperienze offerte non possono essere combinate tra realtà fisiche e digitali. Le esperienze di sovrapposizione della grafica nei flussi video del mondo fisico sono la *realtà aumentata*. Le esperienze che occludere la visualizzazione per presentare un'esperienza digitale sono la *realtà virtuale*. Come si può notare, le esperienze abilitate tra questi due estremi sono la *realtà mista*:
* Iniziando con il mondo fisico, inserire un oggetto digitale, ad esempio un ologramma, come se fosse effettivamente presente.
* A partire dal mondo fisico, una rappresentazione digitale di un'altra persona, un avatar, Mostra la posizione in cui si trovavano quando si lasciavano note. In altre parole, esperienze che rappresentano la collaborazione asincrona in momenti diversi.
* Partendo da un mondo digitale, i limiti fisici del mondo fisico, ad esempio i muri e i mobili, vengono visualizzati digitalmente all'interno dell'esperienza per aiutare gli utenti a evitare gli oggetti fisici.


<br>

![lo spettro di realtà misto](images/mixedrealityspectrum.png)<br>
*Image: lo spettro della realtà mista*

<br>

La realtà più elevata e le offerte di realtà virtuale attualmente disponibili rappresentano una parte molto piccola di questo spettro. Sono, tuttavia, subset del più ampio spettro di realtà mista. Windows 10 è stato creato tenendo conto dell'intero spettro e consente di combinare rappresentazioni digitali di persone, luoghi e cose con il mondo reale.




## <a name="devices-and-experiences"></a>Dispositivi ed esperienze


Esistono due tipi principali di dispositivi che offrono esperienze di realtà mista di Windows:
1. **Dispositivi olografici.** Queste sono caratterizzate dalla capacità del dispositivo di collocare contenuti digitali nel mondo reale come se fossero realmente disponibili.
2. **Dispositivi immersivi.** Queste sono caratterizzate dalla capacità del dispositivo di creare un senso di "presenza", ovvero nascondere il mondo fisico e sostituirlo con un'esperienza digitale.

<table>
<tr>
<th width="30%"> Caratteristica</th><th width="35%"> Dispositivi olografici</th><th width="35%"> Dispositivi immersivi</th>
</tr><tr>
<td><strong>Dispositivo di esempio</strong></td><td> Microsoft HoloLens<br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> Samsung HMD Odyssey +<br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><strong>Display</strong> (Schermo)</td><td> Visualizza-fino alla visualizzazione. Consente all'utente di visualizzare l'ambiente fisico indossando la cuffia.</td><td> Visualizzazione opaca. Blocca l'ambiente fisico mentre è in uso l'auricolare.</td>
</tr><tr>
<td><strong>Spostamento</strong></td><td> Spostamento completo di sei gradi di libertà, rotazione e conversione.</td><td> Spostamento completo di sei gradi di libertà, rotazione e conversione.</td>
</tr>
</table>



Si noti che, se un dispositivo è connesso o collegato a un PC separato (tramite cavo USB o Wi-Fi) o autonomo (senza tethering), non riflette se un dispositivo è olografico o immersivo. Certamente, le funzionalità che migliorano la mobilità comportano una migliore esperienza e i dispositivi olografici e immersivi possono essere collegati o non collegati.


L'avanzamento tecnologico è quello che ha abilitato esperienze di realtà miste. Attualmente non sono presenti dispositivi in grado di eseguire esperienze nell'intero spettro. Tuttavia, Windows 10 offre una piattaforma di realtà mista comune per i produttori e gli sviluppatori di dispositivi. I dispositivi attualmente possono supportare un intervallo specifico all'interno dello spettro della realtà mista. Nel corso del tempo, i nuovi dispositivi espanderanno tale intervallo. In futuro, i dispositivi olografici diventeranno più immersivi e i dispositivi immersivi diventeranno più olografici.

<br>

![i tipi di dispositivo nello spettro di realtà misto](images/Final_WhatIsMixedReality07.png)<br>
*Immagine: dove sono presenti i dispositivi nello spettro della realtà mista*

Spesso è preferibile pensare al tipo di esperienza che uno sviluppatore di applicazioni o giochi vuole creare. In genere, le esperienze sono destinate a un punto o a una parte specifica dello spettro. Gli sviluppatori dovrebbero quindi considerare le funzionalità dei dispositivi di destinazione. Ad esempio, le esperienze che si basano sul mondo fisico vengono eseguite in modo ottimale in HoloLens.
* **Verso sinistra (prossimità della realtà fisica).** Gli utenti rimangono presenti nel proprio ambiente fisico e non sono mai fatti a credere che abbiano lasciato quell'ambiente.
* **Al centro (realtà completamente mista).** Queste esperienze fondono il mondo reale e il mondo digitale. I visualizzatori che hanno visto il film [Jumanji](https://en.wikipedia.org/wiki/Jumanji) possono riconciliare il modo in cui la struttura fisica della casa in cui si è verificata la storia è stata amalgamata con un ambiente Jungle.
* **Verso destra (quasi la realtà digitale).** Gli utenti sperimentano un ambiente completamente digitale e non sono consapevoli di ciò che accade nell'ambiente fisico.


## <a name="see-also"></a>Vedi anche

* [Che cos'è un ologramma?](hologram.md)
* [Informazioni sulle nozioni di base della realtà mista](index.md#understand-the-basics)
* [Avviare la creazione e la creazione di prototipi](design.md)
* [Informazioni sugli strumenti e sull'architettura](development.md)


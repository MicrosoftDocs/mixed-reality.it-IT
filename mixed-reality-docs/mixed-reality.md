---
title: Che cos'è impostato su mixed realtà?
description: Questo articolo definisce realtà mista e viene illustrato dove dispositivi AR e VR semplici, nonché i dispositivi di realtà mista di Windows, ad esempio Microsoft HoloLens e auricolari coinvolgenti di realtà mista di Windows, si trovano nell'ambito di realtà mista.
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: realtà mista, holographic, ar, vr, mr, xr, realtà aumentata, realtà virtuale, spiegazione
ms.openlocfilehash: 3f6000b3d700d7c13f1efa13a81561464f8fdad1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604810"
---
# <a name="what-is-mixed-reality"></a>Che cos'è impostato su mixed realtà?

Realtà mista è il risultato della fusione del mondo fisico con il mondo digitale. Realtà mista è la prossima evoluzione della interazione umana e computer e dell'ambiente e sblocca le possibilità che, prima d'ora, erano limitate a nostro imaginations. Si è resa possibile da miglioramenti di visione artificiale, potenza di elaborazione grafica, tecnologia di visualizzazione e sistemi di input. Il termine *realtà mista* funzionalità originariamente introdotta in un documento 1994 Paul Milgram e Fumio Kishino, "[una tassonomia dei Mixed Visualizza Visual realtà](http://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)." Il documento ha introdotto il concetto del *continuum virtuality* e incentrato sulla modalità di visualizzazione la categorizzazione della tassonomia applicato a. Da allora, le applicazioni di realtà mista va oltre consente di visualizzare ma include anche input ambientali, spaziale audio e posizione.

## <a name="environmental-input-and-perception"></a>Input ambientali e percezione

![Diagramma di Venn di visualizzazione delle interazioni tra esseri umani, ambienti e computer](images/mixed-reality-venn-diagram-300px.png)<br> 

Failover ultimi decenni, la relazione tra input umani e computer input è stata esplorata anche. Contiene anche una disciplina esaminata più nota come *interazione umana computer* o uomo. Input dell'utente avviene tramite svariati modi, tra cui tastiere, mice, touch, input penna, vocale e persino rilevamento di base Kinect.

Miglioramenti di elaborazione e i sensori sono che danno luogo a una nuova area di input del computer da ambienti. L'interazione tra i computer e gli ambienti è conoscenza dell'ambiente in modo efficace, oppure *percezione*. Di conseguenza vengono chiamati i nomi delle API di Windows che rivelano informazioni ambientali il [percezione API](https://docs.microsoft.com/uwp/api/Windows.Perception). Input ambientali acquisisce operazioni come posizione di una persona in tutto il mondo (ad esempio, [rilevamento head](coordinate-systems.md)), aree e confini (ad esempio [mapping spaziale](spatial-mapping.md) e [understanding spaziali](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)), illuminazione, suoni ambientali, riconoscimento dell'oggetto e percorso.

A questo punto, la combinazione di tutti i computer tre – l'elaborazione, input umano e ambientali input: imposta la possibilità di creare esperienze di realtà mista true. Spostamento all'interno del mondo fisico può essere convertita al movimento del mondo digitale. I limiti nel mondo fisico possono influenzare esperienze delle applicazioni, ad esempio di gioco, in tutto il mondo digitale. Senza l'input dell'ambiente, non è possibile blend esperienze tra alla realtà digitale e fisica.

## <a name="the-mixed-reality-spectrum"></a>Lo spettro di realtà mista

Poiché realtà mista è la combinazione del mondo fisico e mondo digitale, ne consegue definiscono le entità finali polare una gamma noto come il continuum virtuality. Per semplicità, si fanno riferimento a questo elemento come il *spettro di realtà mista*. Sul lato sinistro abbiamo realtà fisico in cui il nostro esseri umani, sono presenti. Sul lato destro abbiamo in realtà digitale corrispondente.

<br>

>[!VIDEO https://www.youtube.com/embed/_xpI0JosYUk]

La maggior parte dei telefoni cellulari sul mercato non hanno oggi little a nessuna funzionalità di comprensione dell'ambiente. In questo modo l'esperienza utente che offrono non è possibile combinare tra le realtà digitali e fisiche. L'esperienza utente della sovrimpressione grafica su flussi video del mondo fisico vengono *realtà aumentata*, e le esperienze che nasconde i colori di visualizzazione per offrire un'esperienza digitale sono *realtà virtuale*. Come si può notare, è l'esperienza utente abilitato tra questi due estremi *realtà mista*:
* Inizia con il mondo fisico, l'inserimento di un oggetto digitale, ad esempio ologramma, come se fosse effettivamente presente.
* Inizia con il mondo fisico, una rappresentazione in forma digitale di un'altra persona – un avatar: Mostra la posizione in cui essi sono stati permanente quando si esce da Lotus notes. In altre parole, esperienze che rappresentano la collaborazione asincrona in diversi momenti nel tempo.
* A partire da un mondo digitale, fisici dal mondo fisico, ad esempio pareti e mobili, vengono visualizzati i limiti digitale all'interno di un per consentire agli utenti di evitare gli oggetti fisici.

![Lo spettro di realtà mista](images/mixed-reality-spectrum-550px.png)

Più realtà aumentata e offerte di realtà virtuale disponibili oggi rappresentano una piccola parte di questo spettro. Sono, tuttavia, subset dello spettro realtà mista più grande. Windows 10 viene compilato con l'intero spettro presente e consente la fusione digitale rappresentazioni delle persone, luoghi e cose con il mondo reale.

![Tipi di dispositivi nello spettro di realtà mista](images/mixed-reality-spectrum-device-types-550px.png)

Esistono due tipi principali di dispositivi che offrono esperienze di realtà mista di Windows:
1. **Dispositivi holographic.** Questi sono caratterizzati dalla capacità del dispositivo di inserire contenuto digitale nel mondo reale, come se fosse effettivamente presente.
2. **Dispositivi coinvolgente e concreto.** Questi sono caratterizzati dalla capacità del dispositivo di creazione di un senso di "presenza": se si nasconde il mondo fisico e la relativa sostituzione con un'esperienza digitale.

<table>
<tr>
<th width="20%"> Caratteristica</th><th width="40%"> Dispositivi holographic</th><th width="40%"> Dispositivi coinvolgenti</th>
</tr><tr>
<td> Dispositivo di esempio</td><td> Microsoft HoloLens<br /> <img alt="Microsoft HoloLens image" width="300" height="169" src="images/mshololens-hero1-whitbg-rgb-300px.png" /></td><td> Acer Windows misti realtà Development Edition<br /> <img alt="Acer Windows Mixed Reality Development Edition image" width="300" height="169" src="images/acer-windows-mixed-reality-development-edition-headset-300px.jpg" /></td>
</tr><tr>
<td> Schermo</td><td> <i>Trasparente. la visualizzazione.</i> Consente di vedere ambiente fisico durante indossare l'auricolare.</td><td> <i>Visualizzazione opaca.</i> Esclude l'ambiente fisico durante indossare l'auricolare.</td>
</tr><tr>
<td> Spostamento dei</td><td> Completa lo spostamento dei sei gradi di libertà, sia rotazione e traslazione.</td><td> Completa lo spostamento dei sei gradi di libertà, sia rotazione e traslazione.</td>
</tr>
</table>

Si noti che, se un dispositivo è connesso a o Windows con tethering a un computer separato (tramite cavo USB o Wi-Fi) o autonoma non (senza i limiti) non riflettono se un dispositivo è holographic o coinvolgente e concreto. Certamente, funzionalità che migliorano la mobilità lead a un'esperienza ottimale e coinvolgenti e holographic dispositivi con tethering oppure illimitata.

## <a name="devices-and-experiences"></a>I dispositivi e le esperienze

Tecnologico è ciò che ha abilitato esperienze di realtà mista. Non sono presenti dispositivi subito possano eseguibili esperienze nell'intero spettro; Tuttavia, Windows 10 offre una piattaforma comune di realtà mista per i produttori di dispositivi e sviluppatori. I dispositivi attualmente possono supportare un intervallo specifico all'interno dell'intervallo di realtà mista e nel corso del tempo i nuovi dispositivi devono espandere tale intervallo. In futuro, holographic dispositivi diventerà più coinvolgenti e coinvolgenti dispositivi diventerà più holographic.

![In cui i dispositivi definire il layout nella gamma delle realtà mista](images/mixed-reality-spectrum-device-placement-550px.png)

Spesso, è consigliabile considerare il tipo di esperienza di un'app o giochi sviluppatore desidera creare. L'esperienza utente verranno in genere eseguita in un momento specifico o una parte nella gamma delle. Quindi, gli sviluppatori devono prendere in considerazione le funzionalità dei dispositivi che desiderano di destinazione. Ad esempio, esperienze che si basano sul mondo fisico eseguirà migliore su HoloLens.
* **Verso sinistra (prossimità fisica realtà).** Gli utenti rimarranno disponibili nel proprio ambiente fisico e non vengono apportati a ritenere che hanno lasciato quell'ambiente.
* **Nella parte centrale (realtà mista completamente).** Queste esperienze reali e tutto il mondo digitale perfettamente blend. Gli utenti che hanno visto il film [Jumanji](https://en.wikipedia.org/wiki/Jumanji) possono risolvere le differenze tra la modalità della struttura fisica della casa in cui la storia ha avuto luogo è stata combinata con un ambiente di giungla delle.
* **Verso destra (vicino digitale realtà).** Gli utenti verificano un ambiente completamente digitale e sono a ciò che avviene durante l'ambiente fisico attorno a esse.


## <a name="see-also"></a>Vedere anche
* [Riferimento all'API: Windows.Perception](https://docs.microsoft.com/uwp/api/Windows.Perception)
* [Riferimento all'API: Windows.Perception.Spatial](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial)
* [Riferimento all'API: Windows.Perception.Spatial.Surfaces](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial.Surfaces)

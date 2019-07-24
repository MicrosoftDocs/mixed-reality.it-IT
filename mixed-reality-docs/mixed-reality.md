---
title: Che cos'è la realtà mista?
description: Questo articolo definisce la realtà mista e illustra i dispositivi AR e VR semplici, nonché i dispositivi di realtà mista di Windows, come Microsoft HoloLens e gli auricolari a realtà mista di Windows, che siedono lungo lo spettro della realtà mista.
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: realtà mista, olografica, AR, VR, Mr, XR, realtà aumentata, realtà virtuale, spiegazione
ms.openlocfilehash: fbac8176b36cf28673dd9633cc059e5856a50296
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326306"
---
# <a name="what-is-mixed-reality"></a>Che cos'è la realtà mista?

La realtà mista è il risultato della fusione del mondo fisico con Digiworld. La realtà mista è la prossima evoluzione nell'interazione umana, dei computer e dell'ambiente e consente di sbloccare le possibilità che prima ora erano limitate alla nostra immaginazione. Questo è possibile grazie a miglioramenti in visione artificiale, potenza di elaborazione grafica, tecnologia di visualizzazione e sistemi di input. Il termine *realtà mista* è stato originariamente introdotto in un documento 1994 di Paul Milgram e Fumio Kishino, "[una tassonomia di visualizzazioni visive realtà miste](http://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)". Nel documento è stato introdotto il concetto di *continuità*della virtualizzazione e si è concentrato sul modo in cui viene applicata la categorizzazione della tassonomia. Da allora, l'applicazione della realtà mista va oltre le visualizzazioni. Include anche l'input ambientale, il suono spaziale e la posizione.

## <a name="environmental-input-and-perception"></a>Input e percezione ambientali

![Diagramma di Venn che mostra le interazioni tra computer, persone e ambienti](images/mixed-reality-venn-diagram-300px.png)<br> 

Negli ultimi decenni è stata esplorata la relazione tra l'input umano e il computer. Ha anche una disciplina ampiamente studiata nota come *interazione tra computer umani* o HCI. L'input umano si verifica attraverso un'ampia gamma di mezzi, tra cui tastiere, topi, tocco, input penna, voce e anche rilevamento scheletrico Kinect.

I progressi nei sensori e nell'elaborazione sono la crescita di una nuova area di input del computer dagli ambienti. L'interazione tra computer e ambienti è in effetti la comprensione o la *percezione*ambientale. Di conseguenza, i nomi delle API in Windows che rivelano informazioni ambientali sono detti [API percettive](https://docs.microsoft.com/uwp/api/Windows.Perception). L'input ambientale acquisisce elementi come la posizione di una persona nel mondo, ad esempio il [rilevamento della testa](coordinate-systems.md), le superfici e i limiti (ad esempio, [mapping spaziale](spatial-mapping.md) e [comprensione spaziale](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)), illuminazione ambientale, ambiente acustico, oggetto riconoscimento e percorso.

A questo punto, la combinazione di tutti e tre i computer di elaborazione, input umano e input ambientale: consente di creare esperienze reali miste. Lo spostamento attraverso il mondo fisico può tradursi in movimento nel mondo digitale. I limiti nel mondo fisico possono influenzare le esperienze delle applicazioni, ad esempio giochi, nel mondo digitale. Senza input ambientale, le esperienze non possono essere combinate tra le realtà fisiche e digitali.

## <a name="the-mixed-reality-spectrum"></a>Spettro della realtà mista

Dal momento che la realtà mista unisce i mondi fisici e digitali, queste due realtà definiscono le estremità polari di uno spettro noto come continuità della virtualizzazione. Per semplicità, si fa riferimento a questo come lo spettro della *realtà mista*. Sul lato sinistro è presente la realtà fisica in cui si trovano gli utenti, sul lato destro è disponibile la realtà digitale corrispondente.

<br>

>[!VIDEO https://www.youtube.com/embed/_xpI0JosYUk]

Attualmente la maggior parte dei telefoni cellulari sul mercato non ha alcuna capacità di comprensione ambientale. In questo modo, le esperienze offerte non possono essere combinate tra realtà fisiche e digitali. Le esperienze di sovrapposizione della grafica nei flussi video del mondo fisico sono la *realtà aumentata*. Le esperienze che occludere la visualizzazione per presentare un'esperienza digitale sono la *realtà virtuale*. Come si può notare, le esperienze abilitate tra questi due estremi sono la *realtà mista*:
* Iniziando con il mondo fisico, inserire un oggetto digitale, ad esempio un ologramma, come se fosse effettivamente presente.
* A partire dal mondo fisico, una rappresentazione digitale di un'altra persona, un avatar, Mostra la posizione in cui si trovavano quando si lasciavano note. In altre parole, esperienze che rappresentano la collaborazione asincrona in momenti diversi.
* Partendo da un mondo digitale, i limiti fisici del mondo fisico, ad esempio i muri e i mobili, vengono visualizzati digitalmente all'interno dell'esperienza per aiutare gli utenti a evitare gli oggetti fisici.

![Spettro della realtà mista](images/mixed-reality-spectrum-550px.png)

La realtà più elevata e le offerte di realtà virtuale attualmente disponibili rappresentano una parte molto piccola di questo spettro. Sono, tuttavia, subset del più ampio spettro di realtà mista. Windows 10 è stato creato tenendo conto dell'intero spettro e consente di combinare rappresentazioni digitali di persone, luoghi e cose con il mondo reale.

![Tipi di dispositivi nello spettro della realtà mista](images/mixed-reality-spectrum-device-types-550px.png)

Esistono due tipi principali di dispositivi che offrono esperienze di realtà mista di Windows:
1. **Dispositivi olografici.** Queste sono caratterizzate dalla capacità del dispositivo di collocare contenuti digitali nel mondo reale come se fossero realmente disponibili.
2. **Dispositivi immersivi.** Queste sono caratterizzate dalla capacità del dispositivo di creare un senso di "presenza", ovvero nascondere il mondo fisico e sostituirlo con un'esperienza digitale.

<table>
<tr>
<th width="20%"> Caratteristica</th><th width="40%"> Dispositivi olografici</th><th width="40%"> Dispositivi immersivi</th>
</tr><tr>
<td> Dispositivo di esempio</td><td> Microsoft HoloLens<br /> <img alt="Microsoft HoloLens image" width="300" height="169" src="images/mshololens-hero1-whitbg-rgb-300px.png" /></td><td> Ambiente di sviluppo di realtà mista Acer Windows<br /> <img alt="Acer Windows Mixed Reality Development Edition image" width="300" height="169" src="images/acer-windows-mixed-reality-development-edition-headset-300px.jpg" /></td>
</tr><tr>
<td> Schermo</td><td> <i>Visualizza-fino alla visualizzazione.</i> Consente all'utente di visualizzare l'ambiente fisico indossando la cuffia.</td><td> <i>Visualizzazione opaca.</i> Blocca l'ambiente fisico mentre è in uso l'auricolare.</td>
</tr><tr>
<td> Spostamento</td><td> Spostamento completo di sei gradi di libertà, rotazione e conversione.</td><td> Spostamento completo di sei gradi di libertà, rotazione e conversione.</td>
</tr>
</table>

Si noti che, se un dispositivo è connesso o collegato a un PC separato (tramite cavo USB o Wi-Fi) o autonomo (senza tethering), non riflette se un dispositivo è olografico o immersivo. Certamente, le funzionalità che migliorano la mobilità comportano una migliore esperienza e i dispositivi olografici e immersivi possono essere collegati o non collegati.

## <a name="devices-and-experiences"></a>Dispositivi ed esperienze

L'avanzamento tecnologico è quello che ha abilitato esperienze di realtà miste. Attualmente non sono presenti dispositivi in grado di eseguire esperienze nell'intero spettro. Tuttavia, Windows 10 offre una piattaforma di realtà mista comune per i produttori e gli sviluppatori di dispositivi. I dispositivi attualmente possono supportare un intervallo specifico all'interno dello spettro della realtà mista. Nel corso del tempo, i nuovi dispositivi espanderanno tale intervallo. In futuro, i dispositivi olografici diventeranno più immersivi e i dispositivi immersivi diventeranno più olografici.

![Dove i dispositivi si stabiliscono nello spettro della realtà mista](images/mixed-reality-spectrum-device-placement-550px.png)

Spesso è preferibile pensare al tipo di esperienza che uno sviluppatore di applicazioni o giochi vuole creare. In genere, le esperienze sono destinate a un punto o a una parte specifica dello spettro. Gli sviluppatori dovrebbero quindi considerare le funzionalità dei dispositivi di destinazione. Ad esempio, le esperienze che si basano sul mondo fisico vengono eseguite in modo ottimale in HoloLens.
* **Verso sinistra (prossimità della realtà fisica).** Gli utenti rimangono presenti nel proprio ambiente fisico e non sono mai fatti a credere che abbiano lasciato quell'ambiente.
* **Al centro (realtà completamente mista).** Queste esperienze fondono il mondo reale e il mondo digitale. I visualizzatori che hanno visto il film [Jumanji](https://en.wikipedia.org/wiki/Jumanji) possono riconciliare il modo in cui la struttura fisica della casa in cui si è verificata la storia è stata amalgamata con un ambiente Jungle.
* **Verso destra (quasi la realtà digitale).** Gli utenti sperimentano un ambiente completamente digitale e non sono consapevoli di ciò che accade nell'ambiente fisico.


## <a name="see-also"></a>Vedere anche
* [Informazioni di riferimento sulle API: Windows. percezione](https://docs.microsoft.com/uwp/api/Windows.Perception)
* [Informazioni di riferimento sulle API: Windows. Perception. Spatial](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial)
* [Informazioni di riferimento sulle API: Windows. Perception. Spatial. surfaces](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial.Surfaces)

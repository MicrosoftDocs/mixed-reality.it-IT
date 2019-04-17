---
title: Nozioni fondamentali di interazione
description: Come abbiamo creato esperienze tra HoloLens (dal 1 ° generazione), 2 HoloLens e auricolari coinvolgenti, abbiamo iniziato a scrivere verso il basso alcuni elementi sono stati trovati utile condividere.
author: rwinj
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Progettare l'interazione, realtà mista
ms.openlocfilehash: d594126529b6314a4706f8b6b6af856058c3280a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597552"
---
# <a name="interaction-fundamentals"></a>Nozioni fondamentali di interazione

Come abbiamo creato esperienze in HoloLens e auricolari coinvolgenti, abbiamo iniziato a scrivere verso il basso alcuni elementi che sono stati trovati utile condividere. Pensare a queste informazioni come i blocchi predefiniti fondamentali per la progettazione di interazione di realtà mista.

## <a name="device-support"></a>Supporto di dispositivi

Di seguito è una struttura degli articoli di progettazione di interazione disponibili e il tipo di dispositivo o dei tipi sono applicabili ai.
<br>

<table>

<th>
<tr>

<td style="width:150px;"><strong>Input</strong></td>
<td style="width:150px; text-align: center;"><a href="hololens-hardware-details.md"><strong>HoloLens (dal 1 ° generazione)</strong></a></td>
<td style="width:150px; text-align: center;"><strong>HoloLens 2</strong></td>
<td style="width:150px; text-align: center;"><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
</tr>
</th>
 
<tr>
<td> <a href="gestures.md">Articolati e mani</a></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td><td></td>

</tr><tr>
<td> <a href="gaze-targeting.md">Destinazione rossi</a></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td><td style="text-align: center;"></td>
</tr><tr>
<td> <a href="gaze-targeting.md">Sguardo targeting</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gestures.md">Movimenti</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-design.md">Progettazione vocale</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> Game pad</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr>
<tr>
<td> <a href="motion-controllers.md">Controller di movimento</a></td><td></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>

</tr>
<th>
<tr>
<td style="width:150px;"><strong>Percezione e nuove funzionalità spaziali</strong></td>
<td style="width:150px; text-align: center;"><a href="hololens-hardware-details.md"><strong>HoloLens (dal 1 ° generazione)</strong></a></td>
<td style="width:150px; text-align: center;"><strong>HoloLens 2</strong></td>
<td style="width:150px; text-align: center;"><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
</tr>
</th>
<tr>

<td> <a href="spatial-sound-design.md">Progettazione spaziale</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping-design.md">Progettazione di mapping spaziale</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="hologram.md">Ologrammi</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>

</table>

## <a name="the-user-is-the-camera"></a>L'utente è la fotocamera

![L'utente che corrisponde alla fotocamera](images/useriscamera-640px.jpg)

Considerare sempre sulla progettazione per il punto di vista dell'utente quando vengono spostati sui loro ambienti reali e virtuali.

**Alcune domande da chiedere**
* È l'utente che si trova, schienale, permanente o walking quando si usa l'esperienza?
* La modalità modificare i contenuti in posizioni diverse?
* L'utente può regolare lo?
* L'utente è a proprio agio usando l'app?

**Procedure consigliate**
* L'utente è la fotocamera e controllano lo spostamento. "Let" tali unità.
* Se è necessario per il trasporto praticamente l'utente, essere sensibili a problemi riguardanti il disturbo vestibular.
* Usare le animazioni più breve
* Aggiungere un'animazione da verso il basso/a sinistra/destra o la dissolvenza in entrata invece di Z
* Rallentare temporizzazione
* Consente di visualizzare il mondo in background

**Cosa evitare**
* Non shake della fotocamera o intenzionalmente bloccato a 3DOF (solo l'orientamento, senza conversione), è possibile rendere gli utenti preferisce.
* Nessun movimento improvvisa. Se devi trasferire contenuto da o verso l'utente, spostarlo lentamente e senza problemi verso di loro per la massima comodità. Gli utenti reagirà ai menu di grandi dimensioni presto a tali file.
* Non accelerare o attivare fotocamera dell'utente. Gli utenti sono riservati per l'accelerazione (angular e traslazione).

## <a name="leverage-the-users-perspective"></a>Sfruttare prospettiva dell'utente

Gli utenti vedono il mondo delle realtà mista tramite consente di visualizzare nei dispositivi coinvolgenti e holographic. Nella finestra di HoloLens, questa visualizzazione viene chiamata la [frame holographic](holographic-frame.md).

Nell'ambiente di sviluppo 2D contenuto a cui si accede di frequente e delle impostazioni possono essere inserite negli angoli di una schermata per renderli facilmente accessibili. Tuttavia, holographic le app, il contenuto negli angoli della visualizzazione dell'utente potrà essere prepararli per l'accesso. In questo caso, il centro del frame holographic è il percorso principale per il contenuto.

L'utente potrebbe essere necessario tener conto per agevolare l'individuazione oggetti oltre la visualizzazione immediata o eventi importanti. È possibile utilizzare le frecce, gli itinerari di luce, movimento della testina del carattere, fumetti, puntatori, spaziale audio e istruzioni vocali guideranno l'utente al contenuto importante nell'app.

È consigliabile non blocco contenuto sullo schermo per comodità dell'utente. Se si desidera mantenere il contenuto nella visualizzazione, inserire in tutto il mondo e rendere il contenuto "tag-along", ad esempio il menu Start. Si sentiranno più naturale nell'ambiente di contenuto che viene inserito insieme a prospettiva dell'utente.

![Nel menu start segue la visualizzazione dell'utente quando viene raggiunto il bordo del frame](images/tagalong-1000px.jpg)<br>
*Nel menu Start segue la visualizzazione dell'utente quando viene raggiunto il bordo del frame*

Su HoloLens, vntana sentirsi reale quando rientrano all'interno della cornice holographic poiché essi non tagliate. Gli utenti verranno spostato al fine di determinare i limiti di ologramma all'interno del frame. Su HoloLens, è importante semplificare l'interfaccia utente per rientri in vista dell'utente e mantenere l'attenzione sull'azione principale. Per le cuffie coinvolgenti, è importante mantenere l'illusione di un mondo virtuale persistente all'interno il del dispositivo campo visivo.

## <a name="user-comfort"></a>Fattore di comfort utente

Per garantire la massima [fattore di comfort](comfort.md) sugli schermi montato head, è importante per progettisti e sviluppatori di creare e presentare il contenuto in modo che simuli come esseri umani interpretano le forme 3D e la posizione relativa degli oggetti in naturale World. Dal punto di vista fisico, è anche importante progettare il contenuto che non richiede difficoltoso i movimenti del collo o agli armamenti.

Se lo sviluppo per HoloLens o auricolari coinvolgenti, è importante eseguire il rendering degli oggetti visivi per entrambi gli occhi. Il rendering di una visualizzazione hud un occhio può apportare solo un'interfaccia difficili da comprendere, nonché causare uneasiness occhio e cervello dell'utente.

## <a name="share-your-experience"></a>Condividere la propria esperienza

Usando [acquisizione di realtà mista](mixed-reality-capture.md), gli utenti possono acquisire una foto o video della propria esperienza in qualsiasi momento. Prendere in considerazione esperienze nell'app in cui si desidera incoraggiare gli snapshot o video.

## <a name="leverage-basic-ui-elements-of-the-windows-mixed-reality-home"></a>Usare elementi di base dell'interfaccia utente di casa la realtà mista di Windows

Esattamente come viene avviata l'esperienza di PC Windows con il desktop, realtà mista di Windows viene avviata con la home page. Il [realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md) sfrutta la nostra capacità innata per comprendere e spostarsi tra punti 3D. Con HoloLens, la home page è lo spazio fisico. Con immersive auricolari, la home page è un punto virtuale.

La home page è anche in cui si userà il menu Start aprire e inserire le App e il contenuto. È possibile compilare la home page con contenuto di realtà mista e multitasking con più App contemporaneamente. Le operazioni posizionate in casa rimangono non esiste, anche se si riavvia il dispositivo.

## <a name="see-also"></a>Vedere anche
* [Sguardo targeting](gaze-targeting.md)
* [Movimenti](gestures.md)
* [Progettazione vocale](voice-design.md)
* [Controller di movimento](motion-controllers.md)
* [Progettazione spaziale](spatial-sound-design.md)
* [Progettazione di mapping spaziale](spatial-mapping-design.md)
* [Comfort](comfort.md)
* [Esplorazione di realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md)

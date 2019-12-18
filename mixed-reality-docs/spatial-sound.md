---
title: Audio in realtà mista
description: L'audio in realtà mista può aumentare la confidenza degli utenti nelle interazioni dell'interfaccia utente e immergere gli utenti nell'esperienza.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Audio spaziale, audio surround, audio 3D, audio 3D, audio spaziale
ms.openlocfilehash: b939433daf80a95a11bc0e1ac2ffd75dfe0cf299
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181981"
---
# <a name="audio-in-mixed-reality"></a>Audio in realtà mista
L'audio è una parte essenziale della progettazione e della produttività in realtà mista. Il suono può:
* Aumentare la confidenza degli utenti nelle interazioni con movimento e voce.
* Guida gli utenti ai passaggi successivi.
* Combinare efficacemente gli oggetti virtuali con il mondo reale.

Il rilevamento Head a bassa latenza degli auricolari per la realtà mista, tra cui HoloLens, supporta la spazializzazione basata su HRTF di alta qualità. È possibile spatialize audio nell'applicazione per:
* Richiama l'attenzione sugli elementi visivi.
* Consentire agli utenti di mantenere la consapevolezza degli ambienti reali.

I componenti acustici connettono gli ologrammi al mondo della realtà mista. Fornisce indicazioni sull'ambiente e sullo stato dell'oggetto.

Vedere esempi dettagliati [di progettazione che usa audio](spatial-sound-design.md).

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Spazializzazione</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Accelerazione hardware di spazializzazione</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="use-of-sounds-in-mixed-reality"></a>Uso di suoni in realtà mista
L' [uso di suoni in realtà mista](spatial-sound-design.md) richiede un approccio diverso rispetto alle applicazioni touch e Keyboard-and-mouse. Le decisioni principali relative alla progettazione sono i suoni da spatialize e le interazioni con Sonify. Queste decisioni influiscono fortemente sulla confidenza degli utenti, sulla produttività e sulla curva di apprendimento.

### <a name="case-studies"></a>Case study
HoloTour virtualmente gli utenti a siti turistici e cronologici in tutto il mondo. Vedere la [progettazione audio per HoloTour](case-study-spatial-sound-design-for-holotour.md) case study. Per acquisire gli spazi oggetto sono stati usati un microfono speciale e una configurazione per il rendering.

RoboRaid è uno sparatutto ad alta energia per HoloLens. La [progettazione audio per RoboRaid](case-study-using-spatial-sound-in-roboraid.md) case study descrive le scelte di progettazione effettuate per garantire che l'audio spaziale sia stato usato per l'effetto drammatico più completo.

## <a name="spatialization"></a>Spazializzazione
La spazializzazione è il componente direzionale dell'audio spaziale. Per una configurazione di 7,1 Home Theater, la spazializzazione è semplice come la panoramica tra gli altoparlanti. Tuttavia, per le cuffie in realtà mista, è essenziale usare una tecnologia basata su HRTF per l'accuratezza e la comodità. Windows offre la spazializzazione basata su HRTF e questo supporto è con accelerazione hardware in HoloLens 2.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a>Devo spatialize?
La spazializzazione può migliorare molti suoni nelle applicazioni a realtà mista. La spazializzazione estrae un suono dal capo del listener e lo inserisce nel mondo. Per suggerimenti sull'utilizzo efficace della spazializzazione nell'applicazione, vedere [progettazione di suoni spaziali](spatial-sound-design.md).

### <a name="spatializer-personalization"></a>Personalizzazione di Spatializer
HRTFs manipola le differenze di livello e fase tra le orecchie nello spettro di frequenza. Sono basati su modelli fisici e misurazioni delle forme Head, torso e ear (pinna). I nostri cervelli rispondono a queste differenze per fornire una direzione percepita nel suono.

Ogni persona ha una forma orecchio, una dimensione della testa e una posizione dell'orecchio univoche. Il HRTFs migliore è quindi conforme all'utente. Per aumentare l'accuratezza della spazialità, HoloLens usa la distanza tra gli alunni (dpi) dalle schermate dell'auricolare per modificare il HRTFs per le dimensioni della testa.

### <a name="spatializer-platform-support"></a>Supporto della piattaforma Spatializer
Windows offre la spazializzazione, tra cui HRTFs, tramite l' [API ISpatialAudioClient](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound). Questa API espone l'accelerazione hardware HoloLens 2 HRTF alle applicazioni.

### <a name="spatializer-middleware-support"></a>Supporto del middleware Spatializer
Il supporto per HRTFs di Windows è disponibile per i motori audio di terze parti seguenti.
* Plug-in del [motore audio Unity](spatial-sound-in-unity.md)
* Plug-in del [motore audio Wwise](https://www.audiokinetic.com/products/plug-ins/msspatial/)

## <a name="acoustics"></a>Acustica
L'audio spaziale è più di una direzione. Altre dimensioni includono l'occlusione, l'ostruzione, il riverbero, il portale e la modellazione dell'origine. Complessivamente, queste dimensioni vengono definite *acustiche*. Senza acustica, i suoni spaziali non hanno una distanza percepita.

I trattamenti acustici variano da semplice a molto complesso. È possibile usare un semplice riverbero supportato da qualsiasi motore audio per eseguire il push di suoni spaziali nell'ambiente del listener. I sistemi acustici come l' [acustica del progetto](https://aka.ms/acoustics) offrono un trattamento acustico più completo e accattivante. I progetti acustici possono modellare l'effetto di muri, porte e altra geometria della scena su un suono. Si tratta di un'opzione valida nei casi in cui la geometria della scena pertinente è nota in fase di sviluppo.

## <a name="next-steps"></a>Passaggi successivi
- [Audio spaziale in Unity](spatial-sound-in-unity.md)
- [Come usare un suono in applicazioni in realtà mista](spatial-sound-design.md)

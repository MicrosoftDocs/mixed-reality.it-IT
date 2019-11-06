---
title: Audio in realtà mista
description: L'audio in realtà mista può aumentare la confidenza degli utenti nelle interazioni dell'interfaccia utente e immergere gli utenti nell'esperienza.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Audio spaziale, audio surround, audio 3D, audio 3D, audio spaziale
ms.openlocfilehash: 1930017903439aee3ac53b6c4be344fdc44c356f
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641113"
---
# <a name="audio-in-mixed-reality"></a>Audio in realtà mista
L'audio è una parte essenziale della progettazione e della produttività in realtà mista e può:
* Aumentare la confidenza degli utenti nelle interazioni basate su movimento e voce
* Guida per gli utenti ai passaggi successivi
* Combinare efficacemente oggetti virtuali con il mondo reale

Il rilevamento Head a bassa latenza degli auricolari per la realtà mista, incluso HoloLens, consente l'uso della spazializzazione basata su HRTF di alta qualità. Spatializing audio nell'applicazione può:
* Richiama l'attenzione sugli elementi visivi
* Consentire agli utenti di mantenere la consapevolezza degli ambienti reali

L'aggiunta di acustica in modo più approfondito connette gli ologrammi al mondo misto e può fornire indicazioni sull'ambiente e sullo stato dell'oggetto.

Per esempi più dettagliati di progettazione tramite audio, vedere la pagina relativa alla [progettazione del suono](spatial-sound-design.md).

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

## <a name="using-sounds-in-mixed-reality"></a>Uso di suoni in realtà mista
L' [uso di suoni in realtà mista](spatial-sound-design.md) può richiedere un approccio diverso rispetto alle applicazioni touch e tastiera e mouse. Le decisioni principali relative alla progettazione sono i suoni da spatialize e le interazioni con Sonify. Queste decisioni possono avere un effetto forte sulla confidenza degli utenti, sulla produttività e sulla curva di apprendimento.

### <a name="case-studies"></a>Case study
HoloTour virtualmente gli utenti a siti turistici e cronologici in tutto il mondo. Il case study seguente descrive la progettazione del suono per HoloTour: [Sound Design per HoloTour](case-study-spatial-sound-design-for-holotour.md). Per acquisire gli spazi oggetto sono stati usati un microfono speciale e una configurazione per il rendering.

RoboRaid è uno sparatutto ad alta energia per HoloLens. Il case study seguente descrive le scelte di progettazione effettuate per garantire che l'audio spaziale sia stato usato per un effetto drammatico più completo: [progettazione sonora per RoboRaid](case-study-using-spatial-sound-in-roboraid.md).

## <a name="spatialization"></a>Spazializzazione
La spazializzazione è il componente direzionale dell'audio spaziale. Quando si usa una configurazione di 7,1 Home Theater, la spazializzazione è semplice come la panoramica tra altoparlanti più potenti. Ma con le cuffie in realtà mista è essenziale usare una tecnologia basata su HRTF per l'accuratezza e la comodità. Windows offre la spazializzazione basata su HRTF e questo supporto è con accelerazione hardware in HoloLens 2.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a>Devo spatialize?
Molti suoni nelle applicazioni di realtà mista traggono vantaggio dalla spazializzazione, che estrae un suono dal capo del listener e lo inserisce nel mondo. Per suggerimenti sugli usi più efficaci della spazializzazione nell'applicazione, vedere [progettazione di suoni spaziali](spatial-sound-design.md) .

### <a name="spatializer-personalization"></a>Personalizzazione di Spatializer
HRTFs manipola le differenze di livello e fase tra le orecchie nello spettro di frequenza. Sono basati su modelli fisici e misurazioni delle forme Head, torso e ear (pinna). I nostri cervelli rispondono a queste differenze per dare luogo a una percezione della direzione del suono. 

Ogni persona ha una forma Ear univoca, una dimensione della testa e una posizione dell'orecchio, quindi i HRTFs migliori sono conformi all'utente. HoloLens consente di aumentare l'accuratezza della spazialità usando la distanza tra gli alunni (dpi) dalle cuffie per modificare il HRTFs per le dimensioni della testa.

### <a name="spatializer-platform-support"></a>Supporto della piattaforma Spatializer
Windows offre la spazializzazione, tra cui HRTFs, tramite l' [API ISpatialAudioClient](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound). Questa API espone l'accelerazione hardware HoloLens 2 HRTF alle applicazioni.

### <a name="spatializer-middleware-support"></a>Supporto del middleware Spatializer
Il supporto per HRTFs di Windows è disponibile per alcuni motori audio di terze parti:
* Un plug-in del [motore audio Unity](spatial-sound-in-unity.md) chiama il XAPO HRTF
* Un plug-in del [motore audio Wwise](https://www.audiokinetic.com/products/plug-ins/msspatial/) chiama l'API ISpatialAudioClient

## <a name="acoustics"></a>Acustica
L'audio spaziale può essere più di una direzione. Altre dimensioni, tra cui l'occlusione, l'ostruzione, il riverbero, il portale e la modellazione di origine, sono definite collettivamente "acustica". Senza acustica, i suoni spaziali non hanno una distanza percepita.

Il trattamento acustico può variare da semplice a molto complesso. Utilizzando un semplice riverbero, ad esempio quello supportato da qualsiasi motore audio, è possibile eseguire il push di suoni spaziali nell'ambiente che circonda il listener. Il trattamento acustico più completo e accattivante è disponibile da sistemi acustici come l' [acustica del progetto](https://aka.ms/acoustics). I progetti acustici possono modellare l'effetto di muri, porte e altre geometrie in un suono ed è un'opzione efficace nei casi in cui la geometria della scena pertinente è nota in fase di sviluppo.


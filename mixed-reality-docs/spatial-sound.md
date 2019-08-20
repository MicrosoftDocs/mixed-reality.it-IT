---
title: Audio spaziale
description: L'uso di un suono spaziale in un'applicazione di realtà mista consente di posizionare in modo convincente i suoni in uno spazio 3D.
author: hak0n
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Audio spaziale, audio surround, audio 3D, audio 3D, audio spaziale
ms.openlocfilehash: a30a484c4e47593556fbd1786158262551e11d22
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829926"
---
# <a name="spatial-sound"></a>Audio spaziale

Quando gli oggetti si trovano fuori dalla nostra linea di visione, uno dei modi in cui possiamo percepire il risultato è attraverso il suono. In realtà mista di Windows, il motore audio fornisce il componente uditivo dell'esperienza di realtà mista simulando il suono 3D usando la direzione, la distanza e le simulazioni ambientali. L'uso di un suono spaziale in un'applicazione consente agli sviluppatori di collocare in modo convincente i suoni in uno spazio tridimensionale (Sphere) intorno all'utente. Questi suoni sembreranno come se provenissero da oggetti fisici reali o dagli ologrammi della realtà mista nell'ambiente dell'utente. Dato che gli [ologrammi](hologram.md) sono oggetti costituiti da luce e talvolta acustici, il componente audio aiuta gli ologrammi a renderli più credibili e a creare un'esperienza più coinvolgente.

Anche se gli ologrammi possono essere visualizzati solo visivamente quando lo sguardo dell'utente punta, il suono dell'app può provenire da tutte le direzioni; sopra, sotto, dietro, a fianco e così via. È possibile usare questa funzionalità per attirare l'attenzione su un oggetto che potrebbe non trovarsi attualmente nella visualizzazione dell'utente. Un utente può percepire i suoni da emanare da un'origine nel mondo della realtà mista. Ad esempio, quando l'utente si avvicina a un oggetto o l'oggetto si avvicina, il volume aumenta. Analogamente, quando gli oggetti si muovono intorno a un utente o viceversa, i suoni spaziali offrono l'illusione che i suoni provengono direttamente dall'oggetto.

<br>

>[!VIDEO https://www.youtube.com/embed/PTPvx7mDon4]

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
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Audio spaziale</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (con cuffie)</td>
    </tr>
</table>

## <a name="simulating-the-perceived-location-and-distance-of-sounds"></a>Simulazione della posizione percepita e della distanza dei suoni

Analizzando il modo in cui il suono raggiunge entrambe le orecchie, il cervello determina la distanza e la direzione dell'oggetto che emette il suono. Una HRTF (o funzione di trasferimento correlata alla testa) simula questa interazione modellando la risposta spettrale che caratterizza il modo in cui un orecchio riceve un suono da un punto nello spazio. Il motore audio spaziale USA HRTFs personalizzati per espandere l'esperienza di realtà mista e simulare i suoni provenienti da varie direzioni e distanze.

<br>

>[!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

I segnali audio (Azimut) a sinistra o a destra hanno origine dalle differenze nel tempo che arriva a ogni orecchio. I segnali in su e in giù provengono da modifiche spettrali prodotte dalla forma dell'orecchio esterno (padiglioni). Designando la provenienza dell'audio, il sistema è in grado di simulare l'esperienza del suono in arrivo in momenti diversi. Si noti che in HoloLens, mentre la spazializzazione Azimut è personalizzata, la simulazione dell'elevazione è basata su un set di anthropometrics medio. Pertanto, l'accuratezza dell'elevazione può essere meno accurata dell'accuratezza dell'Azimut.

Anche le caratteristiche dei suoni cambiano in base all'ambiente in cui sono presenti. Ad esempio, se si grida in una grotta, la voce rimbalzerà sulle pareti, i piani e i soffitti, creando un effetto eco. L'impostazione del modello di spazio del suono spaziale riproduce queste riflessioni per inserire i suoni in un ambiente audio particolare. È possibile usare questa impostazione in modo che corrisponda alla posizione effettiva dell'utente per la simulazione di suoni in tale spazio per creare un'esperienza audio più immersiva.

## <a name="integrating-spatial-sound"></a>Integrazione di un suono spaziale

Poiché il principio generale della realtà mista consiste nel radicare gli [ologrammi](hologram.md) nel mondo fisico o nell'ambiente virtuale dell'utente, la maggior parte dei suoni degli ologrammi deve essere spaziali. In HoloLens sono presenti considerazioni di budget per la CPU e la memoria, ma è possibile usare le voci di suono spaziali 10-12 mentre si usa meno di ~ 12% della CPU (~ 70% di uno dei quattro core). L'uso consigliato per le voci spaziali sono:
* Sguardi combinati (evidenziando gli oggetti, in particolare quando sono fuori vista). Quando un ologramma necessita di un'attenzione da un utente, riprodurre un suono sull'ologramma (ad esempio, avere una corteccia del cane virtuale). Questo consente all'utente di trovare l'ologramma quando non è in visualizzazione.
* Audio haptics (audio reattivo per le interazioni non toccate). Ad esempio, riprodurre un suono quando la mano o il controller di movimento dell'utente entra e chiude il frame di movimento. In alternativa, riprodurre un suono quando l'utente seleziona un ologramma.
* Immersione (rumori di ambiente che racchiudono l'utente).

È anche importante notare che, sebbene la fusione di suoni stereo standard con il suono spaziale possa essere efficace per la creazione di ambienti realistici, i suoni stereo dovrebbero essere relativamente tranquilli per lasciare spazio per gli aspetti più sottili del suono spaziale, ad esempio i riflessi ( indicatori di distanza) che possono essere difficili da sentire in un ambiente rumoroso.

Il motore audio spaziale di Windows supporta solo una frequenza di campionamento 48.000 per la riproduzione. La maggior parte del middleware, ad esempio Unity, converte automaticamente i file audio nel formato supportato, ma quando si usano direttamente le API audio di Windows, il formato del contenuto è supportato dall'effetto.

## <a name="see-also"></a>Vedere anche
* [MR Spatial 220](holograms-220.md)
* [Audio spaziale in Unity](spatial-sound-in-unity.md)
* [Audio spaziale in DirectX](spatial-sound-in-directx.md)
* [Progettazione dell'audio spaziale](spatial-sound-design.md)

---
title: Audio spaziale
description: Utilizzo spaziale audio in un'applicazione di realtà mista consente di posizionare convincente suoni nello spazio 3D.
author: hak0n
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: suono spaziale, audio di tipo surround, 3d audio, 3d audio, spaziale audio
ms.openlocfilehash: ccb236a8b53e757ba632a1c7c6cb2d4f07735910
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600833"
---
# <a name="spatial-sound"></a>Audio spaziale

Quando gli oggetti sono da nostri visuale, uno dei modi in cui è possibile percepire cosa sta succedendo intorno a noi è tramite file audio. Nella realtà mista di Windows, il motore di audio fornisce il componente acustico dell'esperienza di realtà mista simulando audio 3D con simulazioni ambientali, distanza e direzione. Utilizzando spaziale audio in un'applicazione consente agli sviluppatori di inserire convincente suoni in uno spazio dimensionale 3 (sfera) per l'utente. Tali suoni risulterà quindi come se provenienti da oggetti fisici reali o vntana la realtà mista nelle vicinanze dell'utente. Dato che [vntana](hologram.md) diventano oggetti di luce e talvolta un suono, il componente audio consente zero vntana rendendoli più credibili e la creazione di un'esperienza più coinvolgente e concreto.

Sebbene vntana può apparire solo in modo visivo in cui fa riferimento sguardo dell'utente, file audio dell'app può provenire da tutte le direzioni; di sopra, sotto, indietro, al lato, e così via. È possibile usare questa funzionalità per attirare l'attenzione su un oggetto che non sia attualmente in vista dell'utente. Un utente può percepire la difficoltà suoni per essere che derivano da un'origine del mondo di realtà mista. Ad esempio, quando l'utente ottiene più da vicino a un oggetto o l'oggetto si avvicina alla loro, aumenta il volume. Analogamente, quando gli oggetti spostano intorno a un utente, o viceversa, suoni spaziali conferire un effetto ottico che suoni provengono direttamente dall'oggetto.

<br>

>[!VIDEO https://www.youtube.com/embed/PTPvx7mDon4]

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Funzionalità</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (dal 1 ° generazione)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>

<td> Audio spaziale</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️ (con le cuffie)</td>

</tr>
</table>

## <a name="simulating-the-perceived-location-and-distance-of-sounds"></a>Simulazione di percorso percepito e distanza di suoni

Grazie all'analisi raggiunge la modalità audio entrambi orecchio, il cervello determina la distanza e direzione dell'oggetto crea l'audio. Un HRTF (o funzione trasferire Related Head) Simula questa interazione tramite la modellazione della risposta spettro che caratterizza come una ear riceve suono da un punto nello spazio. Il motore di audio spatial utilizza HRTFs personalizzate per espandere l'esperienza di realtà mista e simulare i suoni che provengono da varie direzioni e distanze.

<br>

>[!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

Segnali audio sinistro o destro (azimuth) derivano dalle differenze relative al tempo suono arriva a ogni ear. Su e giù segnali derivano dalle modifiche spettrali prodotte dalla forma outer ear (pinnae). Designando in cui audio proviene da, il sistema consente di simulare l'esperienza del suono che arrivano in momenti diversi a orecchio. Si noti che in HoloLens, mentre spatialization azimuth è personalizzato, la simulazione di elevazione dei privilegi è basata su un set di anthropometrics medio. Di conseguenza, la precisione l'elevazione dei privilegi può essere meno accurata rispetto all'accuratezza azimuth.

Le caratteristiche di suoni cambiano anche a seconda dell'ambiente in cui si trovano. Ad esempio, shouting in una proposta causerà la voce per rimbalzi le pareti pavimenti e parte intera superiore, la creazione di un effetto echo. L'impostazione del modello chat room del suono spaziale riproduce questi riflessi per inserire i suoni in un determinato ambiente audio. È possibile usare questa impostazione in modo che corrisponda alla posizione dell'utente effettivo per la simulazione di suoni in tale spazio per creare un'esperienza più coinvolgente e concreto audio.

## <a name="integrating-spatial-sound"></a>L'integrazione di spaziale audio

Poiché il principio generale di realtà mista è quello di forzare a terra [vntana](hologram.md) nel mondo fisico o virtuale ambiente dell'utente, la maggior parte dei suoni vntana dovrebbero essere spatialized. Su HoloLens, esistono naturalmente CPU e memoria budget considerazioni, ma è possibile usare 10 al 12 spaziali audio le voci presenti durante l'utilizzo inferiore a ~ 12% della CPU (circa 70% di uno dei quattro core). Uso consigliato per spaziali audio voices includono:
* Estasiati Mixing (evidenziando oggetti, in particolare quando all'esterno della visualizzazione). Quando un ologrammi necessita di attenzione dell'utente, riprodurre un suono in tali ologrammi (ad esempio, avere una cortecce cane virtuale). Ciò consente all'utente di trovare l'ologrammi quando non è incluso nella visualizzazione.
* Audio Haptics (audio reattivo per le interazioni touchless). Ad esempio, riprodurre un suono quando controller mano o movimento dell'utente entra ed esce dal frame movimento. O riprodurre un suono quando l'utente seleziona ologramma.
* Full immersion (suoni ambiente circostante all'utente).

È anche importante notare che mentre la fusione audio stereo standard spaziali audio possono essere efficace per la creazione di ambienti realistici, i suoni stereo dovrebbero essere relativamente quiet lasciare spazio per gli aspetti meno evidenti del suono spaziale, ad esempio (riflessi distanza segnali) che può essere difficile da poterlo sentire in un ambiente di disturbo.

Motore audio spaziali degli Windows supporta solo una frequenza di campionamento 48 KB per la riproduzione. La maggior parte dei middleware, ad esempio Unity, verrà automaticamente convertire i file audio in formato supportato, ma quando si usa direttamente le API di Audio di Windows, corrisponde al formato del contenuto per il formato supportato dall'effetto.

## <a name="see-also"></a>Vedere anche
* [MR Spatial 220](holograms-220.md)
* [Audio spaziale in Unity](spatial-sound-in-unity.md)
* [Audio spaziale in DirectX](spatial-sound-in-directx.md)
* [Progettazione spaziale](spatial-sound-design.md)

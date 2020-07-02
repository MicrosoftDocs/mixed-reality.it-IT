---
title: Panoramica dello sviluppo con Unreal
description: Panoramica dello sviluppo della realtà mista con Unreal Engine 4
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, beta, streaming, comunicazione remota, realtà mista, sviluppo, guida introduttiva, funzionalità, nuovo progetto, emulatore, documentazione, guide, caratteristiche, ologrammi, sviluppo di giochi
ms.openlocfilehash: 0e3f40c7aa05a9c5f93d7eb9dc9793b6daeb8b90
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720367"
---
# <a name="unreal-development-overview"></a>Panoramica dello sviluppo con Unreal

Muovere i primi passi nelle <a href="https://docs.microsoft.com/en-us/windows/mixed-reality" target="_blank" title="Documentazione sulla realtà mista">applicazioni in realtà mista</a> è un'attività complessa. Nuovi concetti, nuove piattaforme e hardware all'avanguardia possono sembrare ostacoli difficili da superare. Gli sviluppatori che usano Unreal, però, hanno un asso nella manica. Nella <a href="https://docs.unrealengine.com/en-US/Support/Builds/ReleaseNotes/4_25/index.html" target="_blank" title="Note sulla versione di Unreal Engine 4.25">versione</a> più recente di Unreal Engine è incluso il supporto per <a href="https://www.microsoft.com/en-us/windows/windows-mixed-reality" target="_blank" title="Documentazione su Windows Mixed Reality">Windows Mixed Reality</a> (VR) e <a href="https://www.microsoft.com/en-us/hololens/hardware" target="_blank" title="Documentazione su HoloLens 2">HoloLens 2</a> (AR). Questo aggiornamento include:
* Supporto del plug-in UX Tools di Mixed Reality Toolkit
* Supporto di OpenXR
* Comunicazione remota da un'app desktop
* Prestazioni migliori
* Acquisizione in realtà mista (MRC, Mixed Reality Capture)
* Supporto iniziale per Ancoraggi nello spazio di Azure

Se non hai esperienza di sviluppo con Unreal, non iniziare alla cieca. Esplora la <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">serie di esercitazioni</a> su Unreal per acquisire familiarità e cerca risorse e supporto nel <a href="https://www.unrealengine.com/marketplace//store" target="_blank">marketplace</a> di Unreal e nei <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">forum</a> dedicati alla realtà mista. Queste risorse ti consentono di entrare in contatto con la community di sviluppatori e risolutori di problemi che operano oggi sul mercato della realtà mista.

## <a name="mixed-reality-toolkit-for-unreal"></a>Mixed Reality Toolkit per Unreal

[Mixed Reality Toolkit per Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) è un set di componenti progettati per accelerare lo sviluppo in Unreal. Ogni componente include plug-in, esempi e documentazione per la creazione di esperienze immersive. 

[UX Tools per Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) è il primo componente rilasciato ed è attualmente supportato solo su HoloLens 2. Il plug-in del componente include codice, progetti e asset di esempio di funzionalità UX comuni tra cui:
* Simulazione di input
* Attore di interazione manuale
* Componente pulsante a pressione
* Componente manipolatore
* Componente comportamento a seguire

Per approfondire le conoscenze, nel repository GitHub relativo a [UX Tools per Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) puoi trovare dettagli sulle funzionalità e informazioni utili per configurare un progetto.

## <a name="additional-files"></a>File aggiuntivi
Se è la prima volta che crei o distribuisci un'app Unreal per HoloLens, dovrai [scaricare i file di supporto](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch6#packaging-and-deploying-the-app) dal launcher Epic.

## <a name="tutorial"></a>Esercitazione

Il modo migliore per acquisire una nuova competenza è creare qualcosa con le proprie mani. Imparare a [compilare e distribuire una semplice app di scacchi](unreal-uxt-ch1.md) per HoloLens 2 con il plug-in UX Tools è un ottimo punto di partenza. 

La serie di esercitazioni end-to-end offre la possibilità di provare concretamente i componenti e gli scenari UX più comuni. Eseguirai la configurazione di progetto, aggiungendo interazioni alla scena e distribuendo in un dispositivo o in un emulatore. Tutto ciò che serve è Windows 10, un emulatore e Visual Studio 2019.


## <a name="performance"></a>Prestazioni

Lo sviluppo per la realtà mista prevede punti di controllo delle prestazioni che dipendono dalla piattaforma. Un'app HoloLens 2 deve essere eseguita a 60 fotogrammi al secondo perché gli ologrammi risultino stabili e reattivi. I [consigli sulle prestazioni](performance-recommendations-for-unreal.md) forniti da Unreal consentono di soddisfare questo requisito nelle applicazioni.

## <a name="guides-to-specific-features"></a>Guide su funzionalità specifiche

Ci sono diverse funzionalità chiave dello sviluppo per la realtà mista che non vengono trattate nella nostra serie di esercitazioni. Per informazioni dettagliate e applicazioni pratiche, consulta le guide seguenti: 
* [Tracciamento mano](unreal-hand-tracking.md)
* [Tracciamento oculare](unreal-gaze-input.md)
* [Mapping spaziale](unreal-spatial-mapping.md)
* [Ancoraggi nello spazio](unreal-spatial-anchors.md)
* [Input vocale](unreal-voice-input.md)
* [Fotocamera HoloLens](unreal-hololens-camera.md)
* [Codici QR](unreal-qr-codes.md)


## <a name="supported-features"></a>Funzionalità supportate

| Funzionalità di HoloLens 2 | Prima versione di Unreal Engine supportata |
| ----------- | ----------- |
| Supporto per ARM64 | 4.23 |
| Streaming da un PC | 4.23 |
| Mapping spaziale | 4.23 |
| Tracciamento mano e articolazioni | 4.23 |
| Tracciamento oculare | 4.23 |
| Input vocale | 4.23 |
| Ancoraggi nello spazio | 4.23 |
| Accesso alla fotocamera | 4.23 |
| Codici QR | 4.23 |
| Audio spaziale | 4.23 |
| Supporto Spectator Screen per lo streaming | 4.24 |
| LSR planare sullo streaming | 4.24 |
| App di esempio ([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) e [Mission AR](https://docs.unrealengine.com/en-US/Resources/Showcases/MissionAR/index.html)) | 4.24 |
| Mobile Multi-View: prestazioni fino a 60 fps | 4.25 |
| Rendering della terza fotocamera | 4.25 |
| Streaming da un'app desktop in pacchetto | 4.25 |
| Ancoraggi nello spazio di Azure per HoloLens 2 (beta) | 4.25 |
| Supporto per OpenXR (beta) | 4.25 |
| Supporto per UX Tools (0.8) | 4.25 |
| Documentazione ed esercitazioni per sviluppatori | 4.25 |

## <a name="see-also"></a>Vedere anche
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Unreal docs for streaming, deploying to emulator and device</a> (Documentazione su Unreal per lo streaming e la distribuzione in un emulatore e un dispositivo)
* <a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">Unreal performance guidelines for mobile devices</a> (Linee guida sulle prestazioni di Unreal per i dispositivi mobili)

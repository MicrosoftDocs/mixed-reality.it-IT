---
title: Panoramica dello sviluppo con Unreal
description: Panoramica dello sviluppo della realtà mista con Unreal Engine 4
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, beta, streaming, controllo remoto, realtà mista, sviluppo, guida introduttiva, funzionalità, nuovo progetto, emulatore, documentazione, guide, caratteristiche, ologrammi
ms.openlocfilehash: 08ba760acc1a35d8f47de6a7bf6cbc020c8aca3f
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851565"
---
# <a name="unreal-development-overview"></a>Panoramica dello sviluppo con Unreal

Unreal Engine 4 offre ora il supporto completo sia per dispositivi di realtà mista Windows (VR) sia per dispositivi HoloLens 2 (AR). Se non hai familiarità con lo sviluppo in Unreal, l'<a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">introduzione a Unreal Engine 4</a> è un ottimo articolo da cui iniziare. Se hai bisogno di asset, Unreal offre un <a href="https://www.unrealengine.com/marketplace//store" target="_blank">Marketplace</a> completo. 

Dopo aver acquisito le conoscenze di base delle procedure di sviluppo in Unreal, passa all'esercitazione proposta nella sezione successiva per imparare a creare ed eseguire le app in HoloLens. Visita i <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">forum di Unreal relativi alla realtà mista</a> per collaborare con i membri della community impegnati a creare app di realtà mista in Unreal. È il luogo ideale in cui trovare le soluzioni ai problemi che si possono incontrare.

## <a name="tutorial"></a>Esercitazione

Per informazioni su come [compilare e distribuire una semplice app di scacchi](unreal-uxt-ch1.md) per HoloLens 2, segui questa esercitazione end-to-end. Questa esercitazione usa il plug-in UX Tools per accelerare lo sviluppo di app con componenti UX interattivi, tra cui un pulsante e un manipolatore. Per altre informazioni sul plugin UX Tools, vedi la sezione seguente su MRTK. 

## <a name="mixed-reality-toolkit-for-unreal"></a>Mixed Reality Toolkit per Unreal

[Mixed Reality Toolkit per Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) è un set di componenti, sotto forma di plug-in, esempi e documentazione, progettati per accelerare lo sviluppo di applicazioni con realtà mista usando Unreal Engine. Il primo componente rilasciato nell'ambito di questo toolkit è [UX Tools per Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), un plug-in che può essere aggiunto a un progetto HoloLens 2 per integrare funzionalità UX per applicazioni HoloLens 2. La documentazione relativa a Mixed Reality Toolkit e a UX per Unreal è disponibile nei rispettivi repository di GitHub. 

## <a name="performance"></a>Prestazioni

Un'app HoloLens 2 deve essere eseguita a 60 fotogrammi al secondo perché gli ologrammi risultino stabili e reattivi. Per impostare l'app in modo da soddisfare questo requisito, è consigliabile seguire i [consigli sulle prestazioni per Unreal](performance-recommendations-for-unreal.md). 

## <a name="guides-to-specific-features"></a>Guide su funzionalità specifiche

Per informazioni su come usare specifiche funzionalità in Unreal, consulta le guide seguenti: 
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

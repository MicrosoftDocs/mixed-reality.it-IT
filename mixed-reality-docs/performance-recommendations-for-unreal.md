---
title: Consigli sulle prestazioni per Unreal
description: Consigli per ottenere prestazioni ottimali per le app di realtà mista in Unreal
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, prestazioni, ottimizzazione, impostazioni, documentazione
ms.openlocfilehash: 1fab2f714628f61a518d89795cf644e90130200a
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840200"
---
# <a name="performance-recommendations-for-unreal"></a>Consigli sulle prestazioni per Unreal

Questo articolo si basa sugli argomenti affrontati in [Consigli sulle prestazioni per la realtà mista](understanding-performance-for-mixed-reality.md), ma tratta in particolare i concetti specifici dell'ambiente Unreal Engine.

## <a name="recommended-unreal-project-settings"></a>Impostazioni consigliate per il progetto Unreal

- Usa il renderer di realtà virtuale per dispositivi mobili: nelle impostazioni del progetto verifica che la piattaforma di destinazione sia impostata su Mobile/Tablet (Cellulare/Tablet) in Project – Target Hardware (Progetto – Hardware di destinazione)
- Disabilita il culling delle occlusioni: in Engine – Rendering (Motore – Rendering) nella sezione Culling deseleziona Occlusion Culling (Culling di occlusione)
    + Se è necessario il culling delle occlusioni perché devi eseguire il rendering di una scena molto dettagliata, consigliamo di abilitare Support Software Occlusion Culling (Culling di occlusione del software di supporto) in Engine – Rendering (Motore – Rendering). Ciò consente ad Unreal di eseguire il culling delle occlusioni sulla CPU ed evitare query di occlusione della GPU, che influiscono negativamente sulle prestazioni di HoloLens 2.
- Abilita sia Instanced Stereo (Stereo con istanze), sia Mobile Multi-View (Visualizzazioni multiple dispositivi mobili) in Engine – Rendering (Motore – Rendering) nella categoria VR (Realtà virtuale). Potresti dover deselezionare Mobile Post-Processing (Post-elaborazione dispositivi mobili) per poter controllare Mobile Multi-View (Visualizzazioni multiple dispositivi mobili)

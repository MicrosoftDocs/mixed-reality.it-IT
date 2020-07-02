---
title: Consigli sulle prestazioni per Unreal
description: Consigli per ottenere prestazioni ottimali per le app di realtà mista in Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, prestazioni, ottimizzazione, impostazioni, documentazione
ms.openlocfilehash: 9f128a3ef09f29fc745c21b09b7ec97f5db33605
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2020
ms.locfileid: "84533123"
---
# <a name="performance-recommendations-for-unreal"></a>Consigli sulle prestazioni per Unreal

## <a name="overview"></a>Panoramica

Questo articolo si basa sugli argomenti affrontati in [Consigli sulle prestazioni per la realtà mista](understanding-performance-for-mixed-reality.md), ma si concentra in particolare su funzionalità specifiche di Unreal Engine. Prima di proseguire, è consigliabile approfondire le conoscenze sui colli di bottiglia delle applicazioni, sull'analisi e la profilazione delle app in realtà mista e sulle correzioni delle prestazioni generali.

## <a name="recommended-unreal-project-settings"></a>Impostazioni consigliate per il progetto Unreal
Tutte le impostazioni seguenti sono disponibili in **Edit > Project Settings** (Modifica > Impostazioni progetto).

1. Uso del renderer VR per dispositivi mobili:
    * Scorri fino alla sezione **Project** (Progetto), seleziona **Target Hardware** (Hardware di destinazione) e imposta la piattaforma di destinazione su **Mobile/Tablet** (Cellulare/Tablet).

![Impostazione di dispositivi mobili come destinazione](images/unreal/performance-recommendations-img-01.png)

2. Disabilitazione del culling delle occlusioni:
    * Scorri fino alla sezione **Engine** (Motore), seleziona **Rendering**, espandi la sezione **Culling** e deseleziona **Occlusion Culling** (Culling occlusioni).
        + Se è necessario il culling delle occlusioni per il rendering di una scena molto dettagliata, è consigliabile abilitare **Support Software Occlusion Culling** (Supporta culling occlusioni software) in **Engine > Rendering** (Motore > Rendering). Ciò consente ad Unreal di operare sulla CPU ed evitare query di occlusione della GPU, che influiscono negativamente sulle prestazioni di HoloLens 2.

![Impostazione di dispositivi mobili come destinazione](images/unreal/performance-recommendations-img-02.png)

3. Aggiornamento del rendering VR:
    * Scorri fino alla sezione **Engine** (Motore), seleziona **Rendering**, espandi la sezione **VR** e abilita **Instanced Stereo** (Stereo con istanze) e **Mobile Multi-View** (Visualizzazioni multiple dispositivi mobili).
        + Può essere necessario deselezionare **Mobile Post-Processing** (Post-elaborazione dispositivi mobili) per controllare **Mobile Multi-View** (Visualizzazioni multiple dispositivi mobili).

![Impostazione di dispositivi mobili come destinazione](images/unreal/performance-recommendations-img-03.png)

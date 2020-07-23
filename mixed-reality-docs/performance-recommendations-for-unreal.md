---
title: Consigli sulle prestazioni per Unreal
description: Consigli per ottenere prestazioni ottimali per le app di realtà mista in Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, prestazioni, ottimizzazione, impostazioni, documentazione
ms.openlocfilehash: a7972962eeb2b1480a7da38210b5ee77104f508b
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303637"
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

![Disabilitare il culling delle occlusioni](images/unreal/performance-recommendations-img-02.png)

3. Uso delle visualizzazioni multiple dei dispositivi mobili:
    * Scorri fino alla sezione **Engine** (Motore), seleziona **Rendering**, espandi la sezione **VR** e abilita **Instanced Stereo** (Stereo con istanze) e **Mobile Multi-View** (Visualizzazioni multiple dispositivi mobili). L'opzione Mobile HDR (HDR per dispositivi mobili) deve essere deselezionata.

![Impostazioni di rendering VR](images/unreal/performance-recommendations-img-03.png)

4. Impostazione di **Maximum number of CSM cascades to render** (Numero massimo di catene CSM di cui eseguire il rendering) su **1** e di **Max Movable Spotlights / Point Lights** (Numero massimo di riflettori/punti luce mobili) su **0**. 

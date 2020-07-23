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
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="7758c-104">Consigli sulle prestazioni per Unreal</span><span class="sxs-lookup"><span data-stu-id="7758c-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="7758c-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="7758c-105">Overview</span></span>

<span data-ttu-id="7758c-106">Questo articolo si basa sugli argomenti affrontati in [Consigli sulle prestazioni per la realtà mista](understanding-performance-for-mixed-reality.md), ma si concentra in particolare su funzionalità specifiche di Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="7758c-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="7758c-107">Prima di proseguire, è consigliabile approfondire le conoscenze sui colli di bottiglia delle applicazioni, sull'analisi e la profilazione delle app in realtà mista e sulle correzioni delle prestazioni generali.</span><span class="sxs-lookup"><span data-stu-id="7758c-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="7758c-108">Impostazioni consigliate per il progetto Unreal</span><span class="sxs-lookup"><span data-stu-id="7758c-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="7758c-109">Tutte le impostazioni seguenti sono disponibili in **Edit > Project Settings** (Modifica > Impostazioni progetto).</span><span class="sxs-lookup"><span data-stu-id="7758c-109">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="7758c-110">Uso del renderer VR per dispositivi mobili:</span><span class="sxs-lookup"><span data-stu-id="7758c-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="7758c-111">Scorri fino alla sezione **Project** (Progetto), seleziona **Target Hardware** (Hardware di destinazione) e imposta la piattaforma di destinazione su **Mobile/Tablet** (Cellulare/Tablet).</span><span class="sxs-lookup"><span data-stu-id="7758c-111">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![Impostazione di dispositivi mobili come destinazione](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="7758c-113">Disabilitazione del culling delle occlusioni:</span><span class="sxs-lookup"><span data-stu-id="7758c-113">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="7758c-114">Scorri fino alla sezione **Engine** (Motore), seleziona **Rendering**, espandi la sezione **Culling** e deseleziona **Occlusion Culling** (Culling occlusioni).</span><span class="sxs-lookup"><span data-stu-id="7758c-114">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="7758c-115">Se è necessario il culling delle occlusioni per il rendering di una scena molto dettagliata, è consigliabile abilitare **Support Software Occlusion Culling** (Supporta culling occlusioni software) in **Engine > Rendering** (Motore > Rendering).</span><span class="sxs-lookup"><span data-stu-id="7758c-115">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="7758c-116">Ciò consente ad Unreal di operare sulla CPU ed evitare query di occlusione della GPU, che influiscono negativamente sulle prestazioni di HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7758c-116">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>

![Disabilitare il culling delle occlusioni](images/unreal/performance-recommendations-img-02.png)

3. <span data-ttu-id="7758c-118">Uso delle visualizzazioni multiple dei dispositivi mobili:</span><span class="sxs-lookup"><span data-stu-id="7758c-118">Using mobile multi-view:</span></span>
    * <span data-ttu-id="7758c-119">Scorri fino alla sezione **Engine** (Motore), seleziona **Rendering**, espandi la sezione **VR** e abilita **Instanced Stereo** (Stereo con istanze) e **Mobile Multi-View** (Visualizzazioni multiple dispositivi mobili).</span><span class="sxs-lookup"><span data-stu-id="7758c-119">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span> <span data-ttu-id="7758c-120">L'opzione Mobile HDR (HDR per dispositivi mobili) deve essere deselezionata.</span><span class="sxs-lookup"><span data-stu-id="7758c-120">Mobile HDR should be unchecked.</span></span>

![Impostazioni di rendering VR](images/unreal/performance-recommendations-img-03.png)

4. <span data-ttu-id="7758c-122">Impostazione di **Maximum number of CSM cascades to render** (Numero massimo di catene CSM di cui eseguire il rendering) su **1** e di **Max Movable Spotlights / Point Lights** (Numero massimo di riflettori/punti luce mobili) su **0**.</span><span class="sxs-lookup"><span data-stu-id="7758c-122">Setting the **Maximum number of CSM cascades to render** to **1** and **Max Movable Spotlights / Point Lights** to **0**.</span></span> 

---
title: Consigli sulle prestazioni per Unreal
description: Consigli per ottenere prestazioni ottimali per le app di realtà mista in Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, prestazioni, ottimizzazione, impostazioni, documentazione
ms.openlocfilehash: 3c65eb519b57457e6c9e9747af0ad75e6a5e1b4d
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330193"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="07366-104">Consigli sulle prestazioni per Unreal</span><span class="sxs-lookup"><span data-stu-id="07366-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="07366-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="07366-105">Overview</span></span>

<span data-ttu-id="07366-106">Questo articolo si basa sugli argomenti affrontati in [Consigli sulle prestazioni per la realtà mista](understanding-performance-for-mixed-reality.md), ma si concentra in particolare su funzionalità specifiche di Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="07366-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="07366-107">Prima di proseguire, è consigliabile approfondire le conoscenze sui colli di bottiglia delle applicazioni, sull'analisi e la profilazione delle app in realtà mista e sulle correzioni delle prestazioni generali.</span><span class="sxs-lookup"><span data-stu-id="07366-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="07366-108">Impostazioni consigliate per il progetto Unreal</span><span class="sxs-lookup"><span data-stu-id="07366-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="07366-109">Tutte le impostazioni seguenti sono disponibili in **Edit > Project Settings** (Modifica > Impostazioni progetto).</span><span class="sxs-lookup"><span data-stu-id="07366-109">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="07366-110">Uso del renderer VR per dispositivi mobili:</span><span class="sxs-lookup"><span data-stu-id="07366-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="07366-111">Scorri fino alla sezione **Project** (Progetto), seleziona **Target Hardware** (Hardware di destinazione) e imposta la piattaforma di destinazione su **Mobile/Tablet** (Cellulare/Tablet).</span><span class="sxs-lookup"><span data-stu-id="07366-111">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![Impostazione di dispositivi mobili come destinazione](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="07366-113">Disabilitazione del culling delle occlusioni:</span><span class="sxs-lookup"><span data-stu-id="07366-113">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="07366-114">Scorri fino alla sezione **Engine** (Motore), seleziona **Rendering**, espandi la sezione **Culling** e deseleziona **Occlusion Culling** (Culling occlusioni).</span><span class="sxs-lookup"><span data-stu-id="07366-114">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="07366-115">Se è necessario il culling delle occlusioni per il rendering di una scena molto dettagliata, è consigliabile abilitare **Support Software Occlusion Culling** (Supporta culling occlusioni software) in **Engine > Rendering** (Motore > Rendering).</span><span class="sxs-lookup"><span data-stu-id="07366-115">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Cullin** in **Engine > Rendering**.</span></span> <span data-ttu-id="07366-116">Ciò consente ad Unreal di operare sulla CPU ed evitare query di occlusione della GPU, che influiscono negativamente sulle prestazioni di HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="07366-116">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>

![Impostazione di dispositivi mobili come destinazione](images/unreal/performance-recommendations-img-02.png)

3. <span data-ttu-id="07366-118">Aggiornamento del rendering VR:</span><span class="sxs-lookup"><span data-stu-id="07366-118">Updating VR rendering:</span></span>
    * <span data-ttu-id="07366-119">Scorri fino alla sezione **Engine** (Motore), seleziona **Rendering**, espandi la sezione **VR** e abilita **Instanced Stereo** (Stereo con istanze) e **Mobile Multi-View** (Visualizzazioni multiple dispositivi mobili).</span><span class="sxs-lookup"><span data-stu-id="07366-119">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span>
        + <span data-ttu-id="07366-120">Può essere necessario deselezionare **Mobile Post-Processing** (Post-elaborazione dispositivi mobili) per controllare **Mobile Multi-View** (Visualizzazioni multiple dispositivi mobili).</span><span class="sxs-lookup"><span data-stu-id="07366-120">You may need to uncheck **Mobile Post-Processing** in order to be able to check **Mobile Multi-View**</span></span>

![Impostazione di dispositivi mobili come destinazione](images/unreal/performance-recommendations-img-03.png)

---
title: Esercitazioni introduttive - 3. Configurazione dei profili di Mixed Reality Toolkit
description: Questo corso illustra come usare Mixed Reality Toolkit (MRTK) per creare un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: d3381241bb1418fb0e1fb7e5d29d552a533faa32
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376643"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="096c5-105">3. Configurazione dei profili di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="096c5-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="096c5-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="096c5-106">Overview</span></span>

<span data-ttu-id="096c5-107">In questa esercitazione si apprenderà come personalizzare e configurare i profili di MRTK.</span><span class="sxs-lookup"><span data-stu-id="096c5-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="096c5-108">Questo particolare esempio mostrerà come nascondere la mesh di consapevolezza spaziale cambiando le impostazioni dell'osservatore della mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="096c5-108">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="096c5-109">Puoi comunque adottare gli stessi principi per personalizzare le impostazioni o i valori nei profili di MRTK.</span><span class="sxs-lookup"><span data-stu-id="096c5-109">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

## <a name="objectives"></a><span data-ttu-id="096c5-110">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="096c5-110">Objectives</span></span>

* <span data-ttu-id="096c5-111">Imparare a personalizzare e configurare i profili di MRTK</span><span class="sxs-lookup"><span data-stu-id="096c5-111">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="096c5-112">Nascondere il mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="096c5-112">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="096c5-113">Modifica delle opzioni di visualizzazione di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="096c5-113">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="096c5-114">Di seguito sono elencati i passaggi principali da eseguire per nascondere la mesh di consapevolezza spaziale:</span><span class="sxs-lookup"><span data-stu-id="096c5-114">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="096c5-115">Clonare il profilo di configurazione predefinito</span><span class="sxs-lookup"><span data-stu-id="096c5-115">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="096c5-116">Abilitare il sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="096c5-116">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="096c5-117">Clonare il profilo predefinito del sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="096c5-117">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="096c5-118">Clonare il profilo predefinito dell'osservatore della mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="096c5-118">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="096c5-119">Modificare la visibilità della mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="096c5-119">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="096c5-120">per impostazione predefinita, i profili di MRTK non sono modificabili.</span><span class="sxs-lookup"><span data-stu-id="096c5-120">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="096c5-121">Si tratta di modelli di profilo predefiniti che devono essere clonati prima di poter essere modificati.</span><span class="sxs-lookup"><span data-stu-id="096c5-121">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="096c5-122">Sono disponibili diversi livelli annidati di profili.</span><span class="sxs-lookup"><span data-stu-id="096c5-122">There are several nested layers of profiles.</span></span> <span data-ttu-id="096c5-123">È quindi normale clonare e modificare diversi profili quando una o più impostazioni vengono configurate.</span><span class="sxs-lookup"><span data-stu-id="096c5-123">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="096c5-124">1. Clonare il profilo di configurazione predefinito</span><span class="sxs-lookup"><span data-stu-id="096c5-124">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="096c5-125">Il profilo di configurazione è il profilo di primo livello.</span><span class="sxs-lookup"><span data-stu-id="096c5-125">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="096c5-126">Di conseguenza, prima di modificare altri profili, devi clonare il profilo di configurazione.</span><span class="sxs-lookup"><span data-stu-id="096c5-126">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="096c5-127">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) impostare **Configuration Profile** (Profilo di configurazione) di Mixed Reality Toolkit su **DefaultHoloLens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="096c5-127">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="096c5-129">Con l'oggetto **MixedRealityToolkit** ancora selezionato, nella finestra Inspector (Controllo) fai clic sul pulsante **Copy & Customize** (Copia e personalizza) per aprire la finestra Clone Profile (Clona profilo):</span><span class="sxs-lookup"><span data-stu-id="096c5-129">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="096c5-131">Nella finestra Clone Profile (Clona profilo) immettere un **nome di profilo** appropriato, ad esempio _GettingStarted_HoloLens2ConfigurationProfile_ e quindi fare clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultHololens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="096c5-131">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="096c5-133">Il profilo di configurazione appena creato viene ora assegnato come profilo di configurazione per la scena:</span><span class="sxs-lookup"><span data-stu-id="096c5-133">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="096c5-135">Nel menu di Unity scegli **File** > **Save** (Salva) per salvare la scena.</span><span class="sxs-lookup"><span data-stu-id="096c5-135">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="096c5-136">Ricordarsi di salvare il lavoro durante l'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="096c5-136">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="096c5-137">2. Abilitare il sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="096c5-137">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="096c5-138">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) selezionare la scheda **Spatial Awareness** (Consapevolezza spaziale), infine la casella di controllo **Enable Spatial Awareness System** (Abilita sistema di consapevolezza spaziale):</span><span class="sxs-lookup"><span data-stu-id="096c5-138">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="096c5-140">3. Clonare il profilo predefinito del sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="096c5-140">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="096c5-141">Nella scheda **Spatial Awareness** (Consapevolezza spaziale) fai clic sul pulsante **Clone** (Clona) per aprire la finestra Clone Profile (Clona profilo):</span><span class="sxs-lookup"><span data-stu-id="096c5-141">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="096c5-143">Nella finestra Clone Profile (Clona profilo) immettere un **nome di profilo** appropriato, ad esempio _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_ e quindi fare clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="096c5-143">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="096c5-145">Il profilo del sistema di consapevolezza spaziale appena creato viene ora assegnato automaticamente al profilo di configurazione:</span><span class="sxs-lookup"><span data-stu-id="096c5-145">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="096c5-147">4. Clonare il profilo predefinito dell'osservatore della mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="096c5-147">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="096c5-148">Con la scheda **Spatial Awareness** (Consapevolezza spaziale) ancora selezionata, espandi la sezione **Windows Mixed Reality Spatial Mesh Observer** (Osservatore mesh spaziale Windows Mixed Reality) e quindi fai clic sul pulsante **Clone** (Clona) per aprire la finestra Clone Profile (Clona profilo):</span><span class="sxs-lookup"><span data-stu-id="096c5-148">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="096c5-150">Nella finestra Clone Profile (Clona profilo) immettere un **nome di profilo** appropriato, ad esempio _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_ e quindi fare clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span><span class="sxs-lookup"><span data-stu-id="096c5-150">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="096c5-152">Il profilo dell'osservatore della mesh di consapevolezza spaziale appena creato viene ora assegnato automaticamente al profilo del sistema di consapevolezza spaziale:</span><span class="sxs-lookup"><span data-stu-id="096c5-152">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="096c5-154">5. Modificare la visibilità della mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="096c5-154">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="096c5-155">In **Spatial Mesh Observer Settings** (Impostazioni osservatore della mesh spaziale) impostare **Display Option** (Opzione di visualizzazione) su **Occlusion** (Occlusione) per rendere invisibile la mesh di mapping spaziale mentre è ancora funzionante:</span><span class="sxs-lookup"><span data-stu-id="096c5-155">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="096c5-157">Anche se non è visibile, la mesh di mapping spaziale è comunque presente e funzionante.</span><span class="sxs-lookup"><span data-stu-id="096c5-157">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="096c5-158">Ad esempio, gli ologrammi dietro la mesh di mapping spaziale, come nel caso di un ologramma dietro a un muro fisico, non saranno visibili.</span><span class="sxs-lookup"><span data-stu-id="096c5-158">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="096c5-159">hai appreso come modificare un'impostazione nel profilo di MRTK.</span><span class="sxs-lookup"><span data-stu-id="096c5-159">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="096c5-160">Come si può notare, per personalizzare le impostazioni di MRTK, è necessario prima creare copie dei profili predefiniti.</span><span class="sxs-lookup"><span data-stu-id="096c5-160">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="096c5-161">Poiché i profili predefiniti non sono modificabili, saranno sempre presenti come riferimento in caso di ripristino delle impostazioni predefinite.</span><span class="sxs-lookup"><span data-stu-id="096c5-161">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="096c5-162">Per altre informazioni sui profili di MRTK e sulla loro architettura, consultare la [guida alla configurazione dei profili di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="096c5-162">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="096c5-163">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="096c5-163">Congratulations</span></span>

<span data-ttu-id="096c5-164">In questa esercitazione si è appreso come clonare, personalizzare e configurare i profili e le impostazioni di MRTK.</span><span class="sxs-lookup"><span data-stu-id="096c5-164">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

[<span data-ttu-id="096c5-165">Esercitazione successiva: 4. Posizionamento degli oggetti nella scena</span><span class="sxs-lookup"><span data-stu-id="096c5-165">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)

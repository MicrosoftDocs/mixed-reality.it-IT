---
title: Esercitazioni introduttive - 3. Creazione dell'interfaccia utente e configurazione di Mixed Reality Toolkit
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: c389c7a3d16770dcbf57d9acdcfd81c6507f7cd6
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2020
ms.locfileid: "79376138"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a><span data-ttu-id="3dcba-105">3. Creazione dell'interfaccia utente e configurazione di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="3dcba-105">3. Creating user interface and configure Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

<span data-ttu-id="3dcba-106">Nell'esercitazione precedente hai appreso alcune delle funzionalità offerte da Mixed Reality Toolkit (MRTK) avviando la tua prima applicazione per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3dcba-106">In the previous tutorial, you learned about some of the capabilities the Mixed Reality Toolkit (MRTK) has to offer by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="3dcba-107">In questa esercitazione apprenderai come creare e organizzare i pulsanti con i pannelli di testo dell'interfaccia utente e come usare l'interazione predefinita (tocco) per interagire con ogni pulsante.</span><span class="sxs-lookup"><span data-stu-id="3dcba-107">In this tutorial you will learn how to create and organize buttons along with UI text panels, and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="3dcba-108">Potrai inoltre esplorare alcuni effetti e azioni semplici, ad esempio la modifica delle dimensioni, del suono e del colore degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="3dcba-108">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="3dcba-109">Questo modulo presenterà i concetti di base relativi alla modifica dei profili di MRTK, a partire dalla disabilitazione della visibilità della mesh di [mapping spaziale](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="3dcba-109">This module will introduce basic concepts about modifying MRTK profiles, starting with turning off the [spatial mapping](spatial-mapping.md) mesh visualization.</span></span>

## <a name="objectives"></a><span data-ttu-id="3dcba-110">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="3dcba-110">Objectives</span></span>

* <span data-ttu-id="3dcba-111">Personalizzare e configurare i profili di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="3dcba-111">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="3dcba-112">Interagire con gli ologrammi usando pulsanti ed elementi dell'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="3dcba-112">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="3dcba-113">Eseguire interazioni e input di tracciamento delle mani</span><span class="sxs-lookup"><span data-stu-id="3dcba-113">Basic hand-tracking input and interactions</span></span>

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="3dcba-114">Come configurare i profili di Mixed Reality Toolkit (modifica dell'opzione di visualizzazione della mesh di consapevolezza spaziale)</span><span class="sxs-lookup"><span data-stu-id="3dcba-114">How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

<span data-ttu-id="3dcba-115">In questa sezione apprenderai come personalizzare e configurare i profili di MRTK predefiniti.</span><span class="sxs-lookup"><span data-stu-id="3dcba-115">In this section, you will learn how to customize and configure the default MRTK profiles.</span></span>

<span data-ttu-id="3dcba-116">Questo particolare esempio mostrerà come nascondere la mesh di consapevolezza spaziale cambiando le impostazioni dell'osservatore della mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="3dcba-116">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="3dcba-117">Puoi comunque adottare gli stessi principi per personalizzare le impostazioni o i valori nei profili di MRTK.</span><span class="sxs-lookup"><span data-stu-id="3dcba-117">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="3dcba-118">Di seguito sono elencati i passaggi principali da eseguire per nascondere la mesh di consapevolezza spaziale:</span><span class="sxs-lookup"><span data-stu-id="3dcba-118">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="3dcba-119">Clonare il profilo di configurazione predefinito</span><span class="sxs-lookup"><span data-stu-id="3dcba-119">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="3dcba-120">Abilitare il sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="3dcba-120">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="3dcba-121">Clonare il profilo predefinito del sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="3dcba-121">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="3dcba-122">Clonare il profilo predefinito dell'osservatore della mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="3dcba-122">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="3dcba-123">Modificare la visibilità della mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="3dcba-123">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="3dcba-124">per impostazione predefinita, i profili di MRTK non sono modificabili.</span><span class="sxs-lookup"><span data-stu-id="3dcba-124">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="3dcba-125">Si tratta di modelli di profilo predefiniti che devono essere clonati prima di poter essere modificati.</span><span class="sxs-lookup"><span data-stu-id="3dcba-125">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="3dcba-126">Sono disponibili diversi livelli annidati di profili.</span><span class="sxs-lookup"><span data-stu-id="3dcba-126">There are several nested layers of profiles.</span></span> <span data-ttu-id="3dcba-127">È quindi normale clonare e modificare diversi profili quando una o più impostazioni vengono configurate.</span><span class="sxs-lookup"><span data-stu-id="3dcba-127">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="3dcba-128">1. Clonare il profilo di configurazione predefinito</span><span class="sxs-lookup"><span data-stu-id="3dcba-128">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="3dcba-129">Il profilo di configurazione è il profilo di primo livello.</span><span class="sxs-lookup"><span data-stu-id="3dcba-129">The Configuration Profile is the top level profile.</span></span> <span data-ttu-id="3dcba-130">Di conseguenza, prima di modificare altri profili, devi clonare il profilo di configurazione.</span><span class="sxs-lookup"><span data-stu-id="3dcba-130">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="3dcba-131">Con l'oggetto **MixedRealityToolkit** selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) imposta **Configuration Profile** (Profilo di configurazione) di Mixed Reality Toolkit su **DefaultHoloLens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="3dcba-131">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, change the Mixed Reality Toolkit **Configuration Profile** to **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

<span data-ttu-id="3dcba-133">Con l'oggetto **MixedRealityToolkit** ancora selezionato, nella finestra Inspector (Controllo) fai clic sul pulsante **Copy & Customize** (Copia e personalizza) per aprire la finestra Clone Profile (Clona profilo):</span><span class="sxs-lookup"><span data-stu-id="3dcba-133">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

<span data-ttu-id="3dcba-135">Nella finestra Clone Profile (Clona profilo) fai clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultHololens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="3dcba-135">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

<span data-ttu-id="3dcba-137">Il profilo di configurazione appena creato viene ora assegnato come profilo di configurazione per la scena:</span><span class="sxs-lookup"><span data-stu-id="3dcba-137">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

<span data-ttu-id="3dcba-139">Nel menu di Unity scegli **File** > **Save** (Salva) per salvare la scena.</span><span class="sxs-lookup"><span data-stu-id="3dcba-139">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="3dcba-140">Ricorda di salvare il lavoro durante l'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="3dcba-140">Remember to save your work throughout the tutorial.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="3dcba-141">2. Abilitare il sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="3dcba-141">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="3dcba-142">Con l'oggetto **MixedRealityToolkit** ancora selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) seleziona la scheda **Spatial Awareness** (Consapevolezza spaziale) e quindi seleziona la casella di controllo **Enable Spatial Awareness System** (Abilita sistema di consapevolezza spaziale):</span><span class="sxs-lookup"><span data-stu-id="3dcba-142">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="3dcba-144">3. Clonare il profilo predefinito del sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="3dcba-144">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="3dcba-145">Nella scheda **Spatial Awareness** (Consapevolezza spaziale) fai clic sul pulsante **Clone** (Clona) per aprire la finestra Clone Profile (Clona profilo):</span><span class="sxs-lookup"><span data-stu-id="3dcba-145">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

<span data-ttu-id="3dcba-147">Nella finestra Clone Profile (Clona profilo) fai clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="3dcba-147">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

<span data-ttu-id="3dcba-149">Il profilo del sistema di consapevolezza spaziale appena creato viene ora assegnato automaticamente al profilo di configurazione:</span><span class="sxs-lookup"><span data-stu-id="3dcba-149">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="3dcba-151">4. Clonare il profilo predefinito dell'osservatore della mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="3dcba-151">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="3dcba-152">Con la scheda **Spatial Awareness** (Consapevolezza spaziale) ancora selezionata, espandi la sezione **Windows Mixed Reality Spatial Mesh Observer** (Osservatore mesh spaziale Windows Mixed Reality) e quindi fai clic sul pulsante **Clone** (Clona) per aprire la finestra Clone Profile (Clona profilo):</span><span class="sxs-lookup"><span data-stu-id="3dcba-152">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

<span data-ttu-id="3dcba-154">Nella finestra Clone Profile (Clona profilo) fai clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span><span class="sxs-lookup"><span data-stu-id="3dcba-154">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

<span data-ttu-id="3dcba-156">Il profilo dell'osservatore della mesh di consapevolezza spaziale appena creato viene ora assegnato automaticamente al profilo del sistema di consapevolezza spaziale:</span><span class="sxs-lookup"><span data-stu-id="3dcba-156">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="3dcba-158">5. Modificare la visibilità della mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="3dcba-158">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="3dcba-159">In **Spatial Mesh Observer Settings** (Impostazioni osservatore della mesh spaziale) imposta **Display Option** (Opzione di visualizzazione) su **Occlusion** (Occlusione) per rendere invisibile la mesh di mapping spaziale mentre è ancora funzionante:</span><span class="sxs-lookup"><span data-stu-id="3dcba-159">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still being functional:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="3dcba-161">Anche se non è visibile, la mesh di mapping spaziale è comunque presente e funzionante.</span><span class="sxs-lookup"><span data-stu-id="3dcba-161">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="3dcba-162">Ad esempio, gli ologrammi dietro la mesh di mapping spaziale, come nel caso di un ologramma dietro a un muro fisico, non saranno visibili.</span><span class="sxs-lookup"><span data-stu-id="3dcba-162">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="3dcba-163">hai appreso come modificare un'impostazione nel profilo di MRTK.</span><span class="sxs-lookup"><span data-stu-id="3dcba-163">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="3dcba-164">Come puoi notare, per personalizzare le impostazioni di MRTK devi prima creare copie dei profili predefiniti.</span><span class="sxs-lookup"><span data-stu-id="3dcba-164">As you can see, in order to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="3dcba-165">Poiché i profili predefiniti non sono modificabili, li avrai sempre come riferimento se vuoi ripristinare le impostazioni predefinite.</span><span class="sxs-lookup"><span data-stu-id="3dcba-165">Because the default profiles are not editable, you will always have them as reference if you want revert back to the default settings.</span></span> <span data-ttu-id="3dcba-166">Per altre informazioni sui profili di MRTK e sulla loro architettura, puoi consultare la [guida alla configurazione dei profili di Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="3dcba-166">To learn more about MRTK profiles and their architecture, you can visit the [Mixed Reality Toolkit profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="3dcba-167">Movimenti di tracciamento delle mani e pulsanti con supporto per interazioni</span><span class="sxs-lookup"><span data-stu-id="3dcba-167">Hand tracking gestures and interactable buttons</span></span>

<span data-ttu-id="3dcba-168">In questa sezione apprenderai come usare il tracciamento della mano per premere un pulsante e attivare eventi in modo da generare un'azione alla pressione del pulsante.</span><span class="sxs-lookup"><span data-stu-id="3dcba-168">In this section, you will learn how to use hand tracking to press a button and trigger events to cause an action when the button is pressed.</span></span>

<span data-ttu-id="3dcba-169">Questo particolare esempio mostrerà come cambiare il colore di un cubo quando il pulsante viene premuto e come ripristinare il colore originale quando il pulsante viene rilasciato.</span><span class="sxs-lookup"><span data-stu-id="3dcba-169">This particular example will show you how to change the color of a cube when the button is pressed and change it back to it's original color when the button is released.</span></span> <span data-ttu-id="3dcba-170">Puoi comunque adottare gli stessi principi per creare altri eventi.</span><span class="sxs-lookup"><span data-stu-id="3dcba-170">However, you may follow these same principles to create other events.</span></span>

<span data-ttu-id="3dcba-171">Di seguito sono elencati i passaggi principali da eseguire per cambiare il colore del cubo:</span><span class="sxs-lookup"><span data-stu-id="3dcba-171">The main steps you will take to change the color of the cube are:</span></span>

1. <span data-ttu-id="3dcba-172">Aggiungere alla scena il prefab di un pulsante a pressione</span><span class="sxs-lookup"><span data-stu-id="3dcba-172">Add a pressable button prefab to the scene</span></span>
2. <span data-ttu-id="3dcba-173">Aggiungere un cubo alla scena</span><span class="sxs-lookup"><span data-stu-id="3dcba-173">Add a cube to the scene</span></span>
3. <span data-ttu-id="3dcba-174">Configurare il tipo di evento InteractableOnPressReceiver</span><span class="sxs-lookup"><span data-stu-id="3dcba-174">Configure the InteractableOnPressReceiver event type</span></span>
4. <span data-ttu-id="3dcba-175">Configurare il cubo per la ricezione dell'evento On Press</span><span class="sxs-lookup"><span data-stu-id="3dcba-175">Configure the cube to receive the On Press event</span></span>
5. <span data-ttu-id="3dcba-176">Definire l'azione che deve essere attivata dall'evento On Press</span><span class="sxs-lookup"><span data-stu-id="3dcba-176">Define the action to be triggered by the On Press event</span></span>
6. <span data-ttu-id="3dcba-177">Configurare il cubo per la ricezione dell'evento On Release</span><span class="sxs-lookup"><span data-stu-id="3dcba-177">Configure the cube to receive the On Release event</span></span>
7. <span data-ttu-id="3dcba-178">Definire l'azione che deve essere attivata dall'evento On Release</span><span class="sxs-lookup"><span data-stu-id="3dcba-178">Define the action to be triggered by the On Release event</span></span>
8. <span data-ttu-id="3dcba-179">Testare il pulsante usando la simulazione nell'editor</span><span class="sxs-lookup"><span data-stu-id="3dcba-179">Test the button using the in-editor simulation</span></span>

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a><span data-ttu-id="3dcba-180">1. Aggiungere alla scena il prefab di un pulsante a pressione</span><span class="sxs-lookup"><span data-stu-id="3dcba-180">1. Add a pressable button prefab to the scene</span></span>

> [!TIP]
> <span data-ttu-id="3dcba-181">Un <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> è un GameObject preconfigurato che viene archiviato come asset Unity e può essere riutilizzato nel progetto.</span><span class="sxs-lookup"><span data-stu-id="3dcba-181">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="3dcba-182">Nella finestra **Project** (Progetto) cerca **PressableButtonHoloLens2** per individuare il prefab che verrà usato per questo esempio:</span><span class="sxs-lookup"><span data-stu-id="3dcba-182">In the **Project window**, search for **PressableButtonHoloLens2** to locate the prefab you will use for this example:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

<span data-ttu-id="3dcba-184">Nel risultato visualizzato nell'area **Search** (Ricerca) seleziona il prefab **PressableButtonHoloLens2** e **trascinalo** nella finestra **Hierarchy** (Gerarchia) per aggiungerlo alla scena:</span><span class="sxs-lookup"><span data-stu-id="3dcba-184">In the **Search** result, select the **PressableButtonHoloLens2** prefab and **drag** it into the **Hierarchy** window to add it to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="3dcba-186">Per visualizzare la scena come illustrato nell'immagine seguente, fai doppio clic sull'oggetto PressableButtonHoloLens2 nella finestra Hierarchy (Gerarchia) per attivarlo e quindi usa <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a> (Gizmo della scena), nell'angolo superiore destro della finestra della scena, per impostare l'angolo di visualizzazione lungo l'asse Z in avanti.</span><span class="sxs-lookup"><span data-stu-id="3dcba-186">To display your scene as shown in the image below, double-click the PressableButtonHoloLens2 object in the Hierarchy window to bring it into focus, then use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis.</span></span>

<span data-ttu-id="3dcba-187">Con l'oggetto **PressableButtonHoloLens2** ancora selezionato, nella finestra **Inspector** (Controllo):</span><span class="sxs-lookup"><span data-stu-id="3dcba-187">With the **PressableButtonHoloLens2** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="3dcba-188">Modifica il valore di **Position** (Posizione) per Transform (Trasformazione) in modo da posizionare l'oggetto davanti alla fotocamera, che si trova in corrispondenza dell'origine, ad esempio x = 0, y = 0 e z = 0.5</span><span class="sxs-lookup"><span data-stu-id="3dcba-188">Change its Transform **Position** so it's positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="3dcba-190">In generale, 1 unità di posizione in Unity equivale quasi a 1 metro nel mondo fisico.</span><span class="sxs-lookup"><span data-stu-id="3dcba-190">In general, 1 position unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="3dcba-191">Vi sono tuttavia eccezioni, ad esempio quando gli oggetti sono figli di oggetti ridimensionati.</span><span class="sxs-lookup"><span data-stu-id="3dcba-191">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span>

### <a name="2-add-a-cube-to-the-scene"></a><span data-ttu-id="3dcba-192">2. Aggiungere un cubo alla scena</span><span class="sxs-lookup"><span data-stu-id="3dcba-192">2. Add a cube to the scene</span></span>

<span data-ttu-id="3dcba-193">Fai clic con il pulsante destro del mouse in un punto vuoto all'interno della finestra Hierarchy (Gerarchia) e seleziona **3D Object** (Oggetto 3D)  >  **Cube** per aggiungere un cubo alla scena:</span><span class="sxs-lookup"><span data-stu-id="3dcba-193">Right-click on an empty spot inside the Hierarchy window and select **3D Object** > **Cube** to add a cube to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

<span data-ttu-id="3dcba-195">Con l'oggetto **Cube** ancora selezionato, nella finestra **Inspector** (Controllo):</span><span class="sxs-lookup"><span data-stu-id="3dcba-195">With the **Cube** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="3dcba-196">Modifica il valore di **Position** (Posizione) per Transform (Trasformazione) in modo da posizionare il cubo vicino al pulsante a pressione, ma senza sovrapposizioni, ad esempio x = 0, y = 0.04 e z = 0.5</span><span class="sxs-lookup"><span data-stu-id="3dcba-196">Change its Transform **Position** so its located near the pressable button, but not overlapping with it, for example, x = 0, y = 0.04, and z = 0.5</span></span>
* <span data-ttu-id="3dcba-197">Modifica il valore di **Scale** (Ridimensiona) per Transform (Trasformazione) impostando una dimensione appropriata, ad esempio x = 0.02, y = 0.02 e z = 0.02</span><span class="sxs-lookup"><span data-stu-id="3dcba-197">Change its Transform **Scale** to a suitable size, for example, x = 0.02, y = 0.02, and z = 0.02</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a><span data-ttu-id="3dcba-199">3. Configurare il tipo di evento InteractableOnPressReceiver</span><span class="sxs-lookup"><span data-stu-id="3dcba-199">3. Configure the InteractableOnPressReceiver event type</span></span>

<span data-ttu-id="3dcba-200">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **PressableButtonHoloLens2** e quindi nel **menu hamburger** della finestra **Inspector** (Controllo) seleziona **Collapse All Components** (Comprimi tutti i componenti) per ottenere una panoramica di tutti i componenti dell'oggetto:</span><span class="sxs-lookup"><span data-stu-id="3dcba-200">In the Hierarchy window, select the **PressableButtonHoloLens2** object, then in the **Inspector** window **hamburger menu**, select **Collapse All Components** to get an overview of all components on this object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

<span data-ttu-id="3dcba-202">Espandi il componente **Interactable (Script)** e quindi individua ed espandi la sezione **Events** (Eventi) > **Receivers** (Ricevitori):</span><span class="sxs-lookup"><span data-stu-id="3dcba-202">Expand the **Interactable (Script)** component, then locate and expand the **Events** > **Receivers** section:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

<span data-ttu-id="3dcba-204">Fai clic sul pulsante **Add Event** (Aggiungi evento) per creare un nuovo ricevitore di eventi di tipo **InteractableOnPressReceiver**:</span><span class="sxs-lookup"><span data-stu-id="3dcba-204">Click the **Add Event** button, to create a new event receiver of Event Receiver Type **InteractableOnPressReceiver**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> <span data-ttu-id="3dcba-206">Il tipo di ricevitore di eventi denominato InteractableOnPressReceiver consente al pulsante di rispondere a un evento di pressione quando una mano tracciata preme il pulsante.</span><span class="sxs-lookup"><span data-stu-id="3dcba-206">The Event Receiver Type named InteractableOnPressReceiver allows the button to respond to a pressed event when a tracked hand presses the button.</span></span>

<span data-ttu-id="3dcba-207">Per il ricevitore di eventi appena creato, modifica il valore di **Interaction Filter** (Filtro interazioni) impostandolo su **Near and Far** (Vicino e lontano):</span><span class="sxs-lookup"><span data-stu-id="3dcba-207">For the newly created event receiver, change the **Interaction Filter** to **Near and Far**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a><span data-ttu-id="3dcba-209">4. Configurare il cubo per la ricezione dell'evento On Press</span><span class="sxs-lookup"><span data-stu-id="3dcba-209">4. Configure the cube to receive the On Press event</span></span>

<span data-ttu-id="3dcba-210">Dalla finestra Hierarchy (Gerarchia) **fai clic e trascina** l'oggetto **Cube** nel campo dell'oggetto **Event Properties** (Proprietà evento) per l'evento **On Press ()** in modo da assegnare il cubo come ricevitore dell'evento On Press ():</span><span class="sxs-lookup"><span data-stu-id="3dcba-210">From the Hierarchy window, **click-and-drag** the **Cube** into the **Event Properties** object field for the **On Press ()** event to assign the Cube as a receiver of the On Press () event:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a><span data-ttu-id="3dcba-212">5. Definire l'azione che deve essere attivata dall'evento On Press</span><span class="sxs-lookup"><span data-stu-id="3dcba-212">5. Define the action to be triggered by the On Press event</span></span>

<span data-ttu-id="3dcba-213">Fai clic sull'elenco a discesa dell'azione, attualmente impostato su **No Function** (Nessuna funzione), e quindi seleziona **MeshRenderer** > **Material material** (Materiale fisico) per impostare la proprietà del materiale del cubo da modificare quando viene attivato l'evento On Press ():</span><span class="sxs-lookup"><span data-stu-id="3dcba-213">Click the action dropdown, currently assigned **No Function**, and select **MeshRenderer** > **Material material** to set the Cube's material property to be changed when the On Press () event is triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

<span data-ttu-id="3dcba-215">Fai clic sulla piccola icona a forma di **cerchio** accanto al campo del materiale, attualmente impostata su **None (Material)** (Nessuno - Materiale), per aprire la finestra Select Material (Seleziona materiale):</span><span class="sxs-lookup"><span data-stu-id="3dcba-215">Click the small **circle** icon next to the material field, currently populated with **None (Material)**, to open the Select Material window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

<span data-ttu-id="3dcba-217">Nella finestra Select Material (Seleziona materiale) **cerca** **MRTK_Standard** e seleziona un materiale appropriato, ad esempio **MRTK_Standard_Cyan**, in modo che il colore del cubo venga modificato in ciano quando viene premuto il pulsante:</span><span class="sxs-lookup"><span data-stu-id="3dcba-217">In the Select Material window, **search** for **MRTK_Standard** and select a suitable material, for example, **MRTK_Standard_Cyan** so the Cube's color changes to cyan when the button is pressed:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a><span data-ttu-id="3dcba-219">6. Configurare il cubo per la ricezione dell'evento On Release</span><span class="sxs-lookup"><span data-stu-id="3dcba-219">6. Configure the cube to receive the On Release event</span></span>

<span data-ttu-id="3dcba-220">**Ripeti** il passaggio 4 per l'evento On Release per assegnare l'oggetto **Cube** come ricevitore dell'evento **On Release ()** .</span><span class="sxs-lookup"><span data-stu-id="3dcba-220">**Repeat** Step 4 for the On Release event to assign the **Cube** as a receiver of the **On Release ()** event.</span></span>

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a><span data-ttu-id="3dcba-221">7. Definire l'azione che deve essere attivata dall'evento On Release</span><span class="sxs-lookup"><span data-stu-id="3dcba-221">7. Define the action to be triggered by the On Release event</span></span>

<span data-ttu-id="3dcba-222">**Ripeti** il passaggio 5 per l'evento On Release, ma scegli il materiale **MRTK_Standard_LightGray** in modo da ripristinare il colore grigio chiaro originale del cubo quando viene rilasciato il pulsante:</span><span class="sxs-lookup"><span data-stu-id="3dcba-222">**Repeat** Step 5 for the On Release event, but choose the **MRTK_Standard_LightGray** material so the Cube's color returns to its original light gray color when the button is released:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a><span data-ttu-id="3dcba-224">8. Testare il pulsante usando la simulazione nell'editor</span><span class="sxs-lookup"><span data-stu-id="3dcba-224">8. Test the button using the in-editor simulation</span></span>

<span data-ttu-id="3dcba-225">Premi il pulsante **Play** (Riproduci) per attivare la modalità di gioco e usa la simulazione di input nell'editor in modo da testare il pulsante appena configurato.</span><span class="sxs-lookup"><span data-stu-id="3dcba-225">Press the **Play** button to enter Game mode and use the in-editor input simulation to test your newly configured button.</span></span>

<span data-ttu-id="3dcba-226">Pulsante non premuto (barra spaziatrice + rotellina del mouse all'indietro):</span><span class="sxs-lookup"><span data-stu-id="3dcba-226">Button not pressed (spacebar + mouse scroll wheel backward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

<span data-ttu-id="3dcba-228">Pulsante premuto (barra spaziatrice + rotellina del mouse in avanti):</span><span class="sxs-lookup"><span data-stu-id="3dcba-228">Button pressed (spacebar + mouse scroll wheel forward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> <span data-ttu-id="3dcba-230">Per informazioni sulla procedura di simulazione di input nell'editor, puoi fare riferimento alla guida [Uso della simulazione di input manuale nell'editor per testare una scena](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="3dcba-230">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="3dcba-231">Creazione di un pannello di pulsanti con il componente Grid Object Collection di MRTK</span><span class="sxs-lookup"><span data-stu-id="3dcba-231">Creating a panel of buttons using MRTK's Grid Object Collection</span></span>

<span data-ttu-id="3dcba-232">In questa sezione apprenderai come allineare automaticamente più pulsanti in un'interfaccia utente pulita usando il componente Grid Object Collection di MRTK.</span><span class="sxs-lookup"><span data-stu-id="3dcba-232">In this section, you will learn how to automatically align multiple buttons into a neat user interface by using the MRTK's Grid Object Collection tool.</span></span>

<span data-ttu-id="3dcba-233">Questo particolare esempio mostrerà come creare un pannello con cinque pulsanti allineati orizzontalmente.</span><span class="sxs-lookup"><span data-stu-id="3dcba-233">This particular example will show you how to a create a panel with five buttons aligned horizontally.</span></span> <span data-ttu-id="3dcba-234">Puoi tuttavia seguire gli stessi principi per creare altri layout.</span><span class="sxs-lookup"><span data-stu-id="3dcba-234">However, you may follow these same principles to create other layouts.</span></span>

<span data-ttu-id="3dcba-235">Di seguito sono elencati i passaggi principali da eseguire per ottenere questo risultato:</span><span class="sxs-lookup"><span data-stu-id="3dcba-235">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="3dcba-236">Associare gli oggetti pulsante a un oggetto padre</span><span class="sxs-lookup"><span data-stu-id="3dcba-236">Parent the button objects to a parent object</span></span>
2. <span data-ttu-id="3dcba-237">Aggiungere e configurare il componente Grid Object Collection (Script)</span><span class="sxs-lookup"><span data-stu-id="3dcba-237">Add and configure the Grid Object Collection (Script) component</span></span>
3. <span data-ttu-id="3dcba-238">Testare i pulsanti usando la simulazione nell'editor</span><span class="sxs-lookup"><span data-stu-id="3dcba-238">Test the buttons using the in-editor simulation</span></span>

### <a name="1-parent-the-button-objects-to-a-parent-object"></a><span data-ttu-id="3dcba-239">1. Associare gli oggetti pulsante a un oggetto padre</span><span class="sxs-lookup"><span data-stu-id="3dcba-239">1. Parent the button objects to a parent object</span></span>

<span data-ttu-id="3dcba-240">Fai clic con il pulsante destro del mouse in un punto vuoto all'interno della finestra Hierarchy (Gerarchia) e seleziona **Create Empty** (Crea vuoto):</span><span class="sxs-lookup"><span data-stu-id="3dcba-240">Right-click on an empty spot inside the Hierarchy window and select **Create Empty**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

<span data-ttu-id="3dcba-242">Fai clic con il pulsante destro del mouse sull'oggetto appena creato, seleziona **Rename** (Rinomina) e assegnagli un nome appropriato, ad esempio **ButtonCollection**:</span><span class="sxs-lookup"><span data-stu-id="3dcba-242">Right-click on the newly created object, select **Rename**, and give it a suitable name, for example, **ButtonCollection**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

<span data-ttu-id="3dcba-244">Seleziona l'oggetto **PressableButtonHoloLens2** e **trascinalo** sopra l'oggetto **ButtonCollection** per impostarlo come figlio dell'oggetto ButtonCollection:</span><span class="sxs-lookup"><span data-stu-id="3dcba-244">Select the **PressableButtonHoloLens2** object and **drag** it on top of the **ButtonCollection** object to make it a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

<span data-ttu-id="3dcba-246">Fai clic con il pulsante destro del mouse sull'oggetto **PressableButtonHoloLens2** e seleziona **Duplicate** (Duplica) per crearne una copia:</span><span class="sxs-lookup"><span data-stu-id="3dcba-246">Right-click the **PressableButtonHoloLens2** object and select **Duplicate** to create a copy of it:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

<span data-ttu-id="3dcba-248">**Ripeti** questo passaggio altre quattro volte fino a ottenere un totale di cinque oggetti PressableButtonHoloLens2.</span><span class="sxs-lookup"><span data-stu-id="3dcba-248">**Repeat** this step four more times until you have a total of five PressableButtonHoloLens2 objects.</span></span>

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="3dcba-249">2. Aggiungere e configurare il componente Grid Object Collection (Script)</span><span class="sxs-lookup"><span data-stu-id="3dcba-249">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="3dcba-250">Con l'oggetto ButtonCollection selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) fai clic sul pulsante **Add Component** (Aggiungi componente) e quindi cerca e seleziona **Grid Object Collection** (Raccolta oggetti griglia) per aggiungere un componente Grid Object Collection (Script) all'oggetto ButtonCollection:</span><span class="sxs-lookup"><span data-stu-id="3dcba-250">With the ButtonCollection object selected in the Hierarchy window, in the Inspector window, click the **Add Component** button, then search for and select **Grid Object Collection** to add a Grid Object Collection (Script) component to the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

<span data-ttu-id="3dcba-252">Configura il componente Grid Object Collection (Script) nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="3dcba-252">Configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="3dcba-253">Imposta **Num Rows** (Numero righe) su 1 per avere tutti i pulsanti allineati su una sola riga</span><span class="sxs-lookup"><span data-stu-id="3dcba-253">Change **Num Rows** to 1 to have all buttons aligned on one single row</span></span>
* <span data-ttu-id="3dcba-254">Imposta **Cell Width** (Larghezza celle) su 0.05 per spaziare i cubi all'interno della riga</span><span class="sxs-lookup"><span data-stu-id="3dcba-254">Change **Cell Width** to 0.05 to space out the buttons within the row</span></span>

<span data-ttu-id="3dcba-255">Fai quindi clic sul pulsante **Update Collection** (Aggiorna raccolta) per applicare la nuova configurazione:</span><span class="sxs-lookup"><span data-stu-id="3dcba-255">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> <span data-ttu-id="3dcba-257">Le modifiche di configurazione appena applicate rappresentano le modifiche minime necessarie per raggiungere l'obiettivo di posizionare i pulsanti su una sola riga.</span><span class="sxs-lookup"><span data-stu-id="3dcba-257">The configuration changes you just applied represent the minimum changes required to achieve the objective of placing the buttons in a single row.</span></span> <span data-ttu-id="3dcba-258">Nei progetti futuri, tuttavia, a seconda di fattori come l'orientamento degli oggetti padre e figlio, potrebbe essere necessario modificare altre impostazioni, ad esempio il tipo di orientamento.</span><span class="sxs-lookup"><span data-stu-id="3dcba-258">However, in future projects, depending on factors such as, for example, the orientation of the parent and child objects, you might need to adjust other settings such as, for example, the Orient Type.</span></span> <span data-ttu-id="3dcba-259">Per altre informazioni sul componente Grid Object Collection di MRTK, puoi consultare la guida relativa agli [script per la raccolta di oggetti](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="3dcba-259">To learn more about MRTK's Grid Object Collection, you can visit the [Object collection scripts](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

<span data-ttu-id="3dcba-260">Con l'oggetto ButtonCollection ancora selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) modifica il valore di **Position** (Posizione) per Transform (Trasformazione) in modo che gli oggetti pulsante figlio siano posizionati davanti alla fotocamera, che si trova in corrispondenza dell'origine, ad esempio in x = 0, y = 0 e z = 0.5:</span><span class="sxs-lookup"><span data-stu-id="3dcba-260">With the ButtonCollection object still selected in the Hierarchy window, in the Inspector window, change the ButtonCollection object's Transform **Position** so its child button objects are positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> <span data-ttu-id="3dcba-262">Quando hai aggiunto per la prima volta il prefab PressableButtonHoloLens2 alla scena nella sezione precedente [Movimenti di tracciamento delle mani e pulsanti con supporto per interazioni](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons), lo hai posizionato davanti alla fotocamera.</span><span class="sxs-lookup"><span data-stu-id="3dcba-262">When you first added the PressableButtonHoloLens2 prefab to the scene in the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) section above, you positioned it in front of the camera.</span></span> <span data-ttu-id="3dcba-263">Tuttavia, poiché il componente Grid Object Collection controlla la posizione degli oggetti figlio immediati, la posizione Z degli oggetti figlio PressableButtonHoloLens2 è stata reimpostata su 0 in base alla distanza predefinita di Grid Object Collection dal valore padre 0.</span><span class="sxs-lookup"><span data-stu-id="3dcba-263">However, because the Grid Object Collection controls its immediate child objects' position, the PressableButtonHoloLens2 child objects' Z Position were reset to 0 according to the Grid Object Collection's default Distance from parent value of 0.</span></span> <span data-ttu-id="3dcba-264">Questo è il motivo, insieme alla necessità di mantenere organizzata la relazione posizionale padre/figlio, per cui abbiamo spostato in avanti la posizione dell'oggetto ButtonCollection padre anziché configurare la distanza dal valore padre per spostare in avanti gli oggetti figlio PressableButtonHoloLens2.</span><span class="sxs-lookup"><span data-stu-id="3dcba-264">This, and to keep the parent/child positional relationship organized, is why we moved the parent ButtonCollection object's position forward instead of configuring the Distance from parent value to move the PressableButtonHoloLens2 child objects forward.</span></span>

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a><span data-ttu-id="3dcba-265">3. Testare i pulsanti usando la simulazione nell'editor</span><span class="sxs-lookup"><span data-stu-id="3dcba-265">3. Test the buttons using the in-editor simulation</span></span>

<span data-ttu-id="3dcba-266">Fai clic sul pulsante Play (Riproduci) per attivare la modalità di gioco e usa la simulazione di input nell'editor per testare ogni pulsante nel pannello appena creato:</span><span class="sxs-lookup"><span data-stu-id="3dcba-266">Press the Play button to enter Game mode and use the in-editor input simulation to test each of the buttons in in your newly created panel of buttons:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> <span data-ttu-id="3dcba-268">Attualmente, quando premi uno dei cinque pulsanti, il colore del cubo diventa ciano.</span><span class="sxs-lookup"><span data-stu-id="3dcba-268">Currently, when your press any of the five buttons, the cube color changes to cyan.</span></span> <span data-ttu-id="3dcba-269">Per rendere più interessante l'esperienza, usa le informazioni appena apprese per configurare ogni pulsante in modo da assegnare un colore diverso al cubo.</span><span class="sxs-lookup"><span data-stu-id="3dcba-269">To make the experience more interesting, use what you just learn to configure each button to change the cube to a different color.</span></span>

## <a name="adding-text-into-your-scene"></a><span data-ttu-id="3dcba-270">Aggiunta di testo nella scena</span><span class="sxs-lookup"><span data-stu-id="3dcba-270">Adding text into your scene</span></span>

<span data-ttu-id="3dcba-271">In questa sezione apprenderai come aggiungere testo alle esperienze di realtà mista usando TextMesh Pro di Unity, che hai preparato nella sezione [Importare le risorse essenziali TextMesh Pro](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) dell'esercitazione precedente.</span><span class="sxs-lookup"><span data-stu-id="3dcba-271">In this section, you will learn how to add text to your mixed reality experiences using Unity's TextMesh Pro, which you prepared in the [Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) section of the previous tutorial.</span></span>

<span data-ttu-id="3dcba-272">In questo particolare esempio aggiungerai un'etichetta semplice sotto la raccolta di pulsanti creata nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="3dcba-272">In this particular example, you will add a simple label underneath the button collection you created in the previous section.</span></span>

<span data-ttu-id="3dcba-273">Fai clic con il pulsante destro del mouse sull'oggetto ButtonCollection e seleziona **3D Object** (Oggetto 3D) > **Text - TextMeshPro** per creare un oggetto di TextMeshPro come figlio dell'oggetto ButtonCollection:</span><span class="sxs-lookup"><span data-stu-id="3dcba-273">Right-click on the ButtonCollection object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro object as a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

<span data-ttu-id="3dcba-275">Con l'oggetto Text (TMP) di TextMeshPro appena creato ancora selezionato, nella finestra Inspector (Controllo) modifica la posizione e le dimensioni in modo che l'etichetta venga posizionata perfettamente sotto la raccolta di pulsanti, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="3dcba-275">With the newly created TextMeshPro object, named Text (TMP), still selected, in the Inspector window change its position and size so the label is placed neatly underneath the button collection, for example:</span></span>

* <span data-ttu-id="3dcba-276">Modifica il valore di **Pos Y** per Rect Transform (Trasformazione rettangolo) impostando -0.0425</span><span class="sxs-lookup"><span data-stu-id="3dcba-276">Change the Rect Transform **Pos Y** to -0.0425</span></span>
* <span data-ttu-id="3dcba-277">Modifica il valore di **Width** (Larghezza) per Rect Transform (Trasformazione rettangolo) impostando 0.24</span><span class="sxs-lookup"><span data-stu-id="3dcba-277">Change the Rect Transform **Width** to 0.24</span></span>
* <span data-ttu-id="3dcba-278">Modifica il valore di **Height** (Altezza) per Rect Transform (Trasformazione rettangolo) impostando 0.024</span><span class="sxs-lookup"><span data-stu-id="3dcba-278">Change the Rect Transform **Height** to 0.024</span></span>

<span data-ttu-id="3dcba-279">Aggiorna quindi il testo in base a ciò che indica l'etichetta e scegli le proprietà del tipo di carattere, in modo da adattare il testo all'etichetta, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="3dcba-279">Then update the text to reflect what the label is for and choose font properties so the text fits within the label, for example:</span></span>

* <span data-ttu-id="3dcba-280">Modifica il valore di **Text** (Testo) per Text Mesh Pro (Script) impostando Button Collection</span><span class="sxs-lookup"><span data-stu-id="3dcba-280">Change the Text Mesh Pro (Script) **Text** to Button Collection</span></span>
* <span data-ttu-id="3dcba-281">Modifica il valore di **Font Style** (Stile carattere) per Text Mesh Pro (Script) impostando Bold (Grassetto)</span><span class="sxs-lookup"><span data-stu-id="3dcba-281">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="3dcba-282">Modifica il valore di **Font Size** (Dimensione carattere) per Text Mesh Pro (Script) impostando 0.2</span><span class="sxs-lookup"><span data-stu-id="3dcba-282">Change the Text Mesh Pro (Script) **Font Size** to 0.2</span></span>
* <span data-ttu-id="3dcba-283">Modifica il valore di **Alignment** (Allineamento) impostando Center (Al centro) e Middle (In mezzo)</span><span class="sxs-lookup"><span data-stu-id="3dcba-283">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="3dcba-285">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="3dcba-285">Congratulations</span></span>

<span data-ttu-id="3dcba-286">In questa esercitazione hai appreso come clonare, personalizzare e configurare un'impostazione di profilo MRTK.</span><span class="sxs-lookup"><span data-stu-id="3dcba-286">In this tutorial, you learned how to clone, customize, and configure an MRTK profile setting.</span></span> <span data-ttu-id="3dcba-287">Hai inoltre appreso come interagire con i pulsanti per attivare gli eventi usando le mani tracciate sul dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3dcba-287">You also learned how to interact with buttons to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="3dcba-288">e, infine, come creare un'interfaccia utente semplice usando i componenti Grid Object Collection di MRTK e Text Mesh Pro di Unity.</span><span class="sxs-lookup"><span data-stu-id="3dcba-288">Finally, you learned how to create a simple UI interface using the MRTK's Grid Object Collection component and Unity's Text Mesh Pro.</span></span>

[<span data-ttu-id="3dcba-289">Esercitazione successiva: 4. Inserimento di contenuto dinamico e uso dei risolutori</span><span class="sxs-lookup"><span data-stu-id="3dcba-289">Next Tutorial: 4. Placing dynamic content and using solvers</span></span>](mrlearning-base-ch3.md)

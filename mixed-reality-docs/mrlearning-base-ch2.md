---
title: Esercitazioni introduttive-3. Creazione dell'interfaccia utente e configurazione del Toolkit per realtà mista
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: f1d042150d1c81940e672b174c6c02ac71e05883
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554882"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a><span data-ttu-id="b6c99-105">3. creazione dell'interfaccia utente e configurazione del Toolkit per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="b6c99-105">3. Creating user interface and configure Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

<span data-ttu-id="b6c99-106">Nell'esercitazione precedente sono state illustrate alcune delle funzionalità offerte dal Toolkit di realtà mista (MRTK) avviando la prima applicazione per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b6c99-106">In the previous tutorial, you learned about some of the capabilities the Mixed Reality Toolkit (MRTK) has to offer by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="b6c99-107">In questa esercitazione si apprenderà come creare e organizzare i pulsanti insieme ai pannelli di testo dell'interfaccia utente e come usare l'interazione predefinita (tocco) per interagire con ogni pulsante.</span><span class="sxs-lookup"><span data-stu-id="b6c99-107">In this tutorial you will learn how to create and organize buttons along with UI text panels, and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="b6c99-108">Potrai inoltre esplorare alcuni effetti e azioni semplici, ad esempio la modifica delle dimensioni, del suono e del colore degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="b6c99-108">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="b6c99-109">Questo modulo introduce i concetti di base sulla modifica dei profili MRTK, a partire dalla disattivazione della visualizzazione Mesh di [mapping spaziale](spatial-mapping.md) .</span><span class="sxs-lookup"><span data-stu-id="b6c99-109">This module will introduce basic concepts about modifying MRTK profiles, starting with turning off the [spatial mapping](spatial-mapping.md) mesh visualization.</span></span>

## <a name="objectives"></a><span data-ttu-id="b6c99-110">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="b6c99-110">Objectives</span></span>

* <span data-ttu-id="b6c99-111">Personalizzare e configurare i profili di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="b6c99-111">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="b6c99-112">Interagire con gli ologrammi usando gli elementi e i pulsanti dell'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="b6c99-112">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="b6c99-113">Eseguire interazioni e input di tracciamento delle mani</span><span class="sxs-lookup"><span data-stu-id="b6c99-113">Basic hand-tracking input and interactions</span></span>

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="b6c99-114">Come configurare i profili del Toolkit di realtà mista (opzione di visualizzazione modifica consapevolezza spaziale)</span><span class="sxs-lookup"><span data-stu-id="b6c99-114">How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

<span data-ttu-id="b6c99-115">In questa sezione si apprenderà come personalizzare e configurare i profili MRTK predefiniti.</span><span class="sxs-lookup"><span data-stu-id="b6c99-115">In this section, you will learn how to customize and configure the default MRTK profiles.</span></span>

<span data-ttu-id="b6c99-116">Questo particolare esempio Mostra come nascondere la mesh di riconoscimento spaziale cambiando le impostazioni dell'osservatore mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="b6c99-116">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="b6c99-117">Tuttavia, è possibile seguire questi stessi principi per personalizzare qualsiasi impostazione o valore nei profili MRTK.</span><span class="sxs-lookup"><span data-stu-id="b6c99-117">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="b6c99-118">I passaggi principali da eseguire per nascondere la mesh di riconoscimento spaziale sono:</span><span class="sxs-lookup"><span data-stu-id="b6c99-118">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="b6c99-119">Clonare il profilo di configurazione predefinito</span><span class="sxs-lookup"><span data-stu-id="b6c99-119">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="b6c99-120">Abilitare il sistema di riconoscimento spaziale</span><span class="sxs-lookup"><span data-stu-id="b6c99-120">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="b6c99-121">Clonare il profilo di sistema di riconoscimento spaziale predefinito</span><span class="sxs-lookup"><span data-stu-id="b6c99-121">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="b6c99-122">Clonare il profilo dell'osservatore mesh di riconoscimento spaziale predefinito</span><span class="sxs-lookup"><span data-stu-id="b6c99-122">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="b6c99-123">Modificare la visibilità della mesh di riconoscimento spaziale</span><span class="sxs-lookup"><span data-stu-id="b6c99-123">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="b6c99-124">per impostazione predefinita, i profili di MRTK non sono modificabili.</span><span class="sxs-lookup"><span data-stu-id="b6c99-124">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="b6c99-125">Si tratta di modelli di profilo predefiniti che è necessario clonare prima che possano essere modificati.</span><span class="sxs-lookup"><span data-stu-id="b6c99-125">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="b6c99-126">Sono disponibili diversi livelli annidati di profili.</span><span class="sxs-lookup"><span data-stu-id="b6c99-126">There are several nested layers of profiles.</span></span> <span data-ttu-id="b6c99-127">È quindi normale clonare e modificare diversi profili quando si configurano una o più impostazioni.</span><span class="sxs-lookup"><span data-stu-id="b6c99-127">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="b6c99-128">1. clonare il profilo di configurazione predefinito</span><span class="sxs-lookup"><span data-stu-id="b6c99-128">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="b6c99-129">Il profilo di configurazione è il profilo di primo livello.</span><span class="sxs-lookup"><span data-stu-id="b6c99-129">The Configuration Profile is the top level profile.</span></span> <span data-ttu-id="b6c99-130">Di conseguenza, per poter modificare altri profili, è necessario prima clonare il profilo di configurazione.</span><span class="sxs-lookup"><span data-stu-id="b6c99-130">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="b6c99-131">Con l'oggetto **MixedRealityToolkit** selezionato nella finestra gerarchia, nella finestra Inspector modificare il **profilo di configurazione** del Toolkit di realtà mista in **DefaultHoloLens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="b6c99-131">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, change the Mixed Reality Toolkit **Configuration Profile** to **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

<span data-ttu-id="b6c99-133">Con l'oggetto **MixedRealityToolkit** ancora selezionato, nella finestra di controllo fare clic sul pulsante **copia & Personalizza** per aprire la finestra profilo Clone:</span><span class="sxs-lookup"><span data-stu-id="b6c99-133">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

<span data-ttu-id="b6c99-135">Nella finestra profilo clone fare clic sul pulsante **clona** per creare una copia modificabile di **DefaultHololens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="b6c99-135">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

<span data-ttu-id="b6c99-137">Il profilo di configurazione appena creato viene ora assegnato come profilo di configurazione per la scena:</span><span class="sxs-lookup"><span data-stu-id="b6c99-137">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

<span data-ttu-id="b6c99-139">Nel menu Unity selezionare **File** > **Salva** per salvare la scena.</span><span class="sxs-lookup"><span data-stu-id="b6c99-139">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="b6c99-140">Ricordarsi di salvare il lavoro durante l'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="b6c99-140">Remember to save your work throughout the tutorial.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="b6c99-141">2. abilitare il sistema di riconoscimento spaziale</span><span class="sxs-lookup"><span data-stu-id="b6c99-141">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="b6c99-142">Con l'oggetto **MixedRealityToolkit** ancora selezionato nella finestra gerarchia, nella finestra di controllo selezionare la scheda **consapevolezza spaziale** e quindi selezionare la casella di controllo **Abilita sistema di riconoscimento spaziale** :</span><span class="sxs-lookup"><span data-stu-id="b6c99-142">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="b6c99-144">3. clonare il profilo di sistema di riconoscimento spaziale predefinito</span><span class="sxs-lookup"><span data-stu-id="b6c99-144">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="b6c99-145">Nella scheda **sensibilizzazione spaziale** fare clic sul pulsante **clona** per aprire la finestra profilo Clone:</span><span class="sxs-lookup"><span data-stu-id="b6c99-145">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

<span data-ttu-id="b6c99-147">Nella finestra profilo clone fare clic sul pulsante **clona** per creare una copia modificabile di **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="b6c99-147">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

<span data-ttu-id="b6c99-149">Il profilo del sistema di riconoscimento spaziale appena creato viene ora assegnato automaticamente al profilo di configurazione:</span><span class="sxs-lookup"><span data-stu-id="b6c99-149">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="b6c99-151">4. clonare il profilo dell'osservatore mesh di riconoscimento spaziale predefinito</span><span class="sxs-lookup"><span data-stu-id="b6c99-151">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="b6c99-152">Con la scheda **consapevolezza spaziale** ancora selezionata, espandere la sezione visualizzatore **mesh della realtà mista di Windows** , quindi fare clic sul pulsante **clona** per aprire la finestra profilo Clone:</span><span class="sxs-lookup"><span data-stu-id="b6c99-152">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

<span data-ttu-id="b6c99-154">Nella finestra profilo clone fare clic sul pulsante **clona** per creare una copia modificabile di **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span><span class="sxs-lookup"><span data-stu-id="b6c99-154">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

<span data-ttu-id="b6c99-156">Il profilo dell'osservatore mesh di consapevolezza spaziale appena creato viene assegnato automaticamente al profilo del sistema di riconoscimento spaziale:</span><span class="sxs-lookup"><span data-stu-id="b6c99-156">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="b6c99-158">5. modificare la visibilità della mesh di riconoscimento spaziale</span><span class="sxs-lookup"><span data-stu-id="b6c99-158">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="b6c99-159">Nelle **impostazioni dell'osservatore mesh spaziale**modificare l' **opzione di visualizzazione** in **occlusione** per rendere invisibile la mesh del mapping spaziale mentre è ancora funzionante:</span><span class="sxs-lookup"><span data-stu-id="b6c99-159">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still being functional:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="b6c99-161">Sebbene la mesh di mapping spaziale non sia visibile, è ancora presente e funzionante.</span><span class="sxs-lookup"><span data-stu-id="b6c99-161">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="b6c99-162">Ad esempio, tutti gli ologrammi dietro la mesh di mapping spaziale, ad esempio un ologramma dietro a un muro fisico, non saranno visibili.</span><span class="sxs-lookup"><span data-stu-id="b6c99-162">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="b6c99-163">hai appreso come modificare un'impostazione nel profilo di MRTK.</span><span class="sxs-lookup"><span data-stu-id="b6c99-163">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="b6c99-164">Come si può notare, per personalizzare le impostazioni MRTK, è necessario creare prima di tutto le copie dei profili predefiniti.</span><span class="sxs-lookup"><span data-stu-id="b6c99-164">As you can see, in order to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="b6c99-165">Poiché i profili predefiniti non sono modificabili, verranno sempre restituiti come riferimento se si desidera ripristinare le impostazioni predefinite.</span><span class="sxs-lookup"><span data-stu-id="b6c99-165">Because the default profiles are not editable, you will always have them as reference if you want revert back to the default settings.</span></span> <span data-ttu-id="b6c99-166">Per altre informazioni sui profili di MRTK e sulla relativa architettura, vedere la [Guida alla configurazione del profilo del Toolkit di realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="b6c99-166">To learn more about MRTK profiles and their architecture, you can visit the [Mixed Reality Toolkit profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="b6c99-167">Movimenti di rilevamento della mano e pulsanti interagiscono</span><span class="sxs-lookup"><span data-stu-id="b6c99-167">Hand tracking gestures and interactable buttons</span></span>

<span data-ttu-id="b6c99-168">In questa sezione si apprenderà come usare il rilevamento della mano per premere un pulsante e attivare gli eventi per generare un'azione quando viene premuto il pulsante.</span><span class="sxs-lookup"><span data-stu-id="b6c99-168">In this section, you will learn how to use hand tracking to press a button and trigger events to cause an action when the button is pressed.</span></span>

<span data-ttu-id="b6c99-169">In questo particolare esempio viene illustrato come modificare il colore di un cubo quando si preme il pulsante e tornare al colore originale quando si rilascia il pulsante.</span><span class="sxs-lookup"><span data-stu-id="b6c99-169">This particular example will show you how to change the color of a cube when the button is pressed and change it back to it's original color when the button is released.</span></span> <span data-ttu-id="b6c99-170">Tuttavia, è possibile seguire questi stessi principi per la creazione di altri eventi.</span><span class="sxs-lookup"><span data-stu-id="b6c99-170">However, you may follow these same principles to create other events.</span></span>

<span data-ttu-id="b6c99-171">I passaggi principali da seguire per modificare il colore del cubo sono:</span><span class="sxs-lookup"><span data-stu-id="b6c99-171">The main steps you will take to change the color of the cube are:</span></span>

1. <span data-ttu-id="b6c99-172">Aggiungere un pulsante stampabile prefabbricato alla scena</span><span class="sxs-lookup"><span data-stu-id="b6c99-172">Add a pressable button prefab to the scene</span></span>
2. <span data-ttu-id="b6c99-173">Aggiungere un cubo alla scena</span><span class="sxs-lookup"><span data-stu-id="b6c99-173">Add a cube to the scene</span></span>
3. <span data-ttu-id="b6c99-174">Configurare il tipo di evento InteractableOnPressReceiver</span><span class="sxs-lookup"><span data-stu-id="b6c99-174">Configure the InteractableOnPressReceiver event type</span></span>
4. <span data-ttu-id="b6c99-175">Configurare il cubo per la ricezione dell'evento di stampa</span><span class="sxs-lookup"><span data-stu-id="b6c99-175">Configure the cube to receive the On Press event</span></span>
5. <span data-ttu-id="b6c99-176">Definire l'azione che deve essere attivata dall'evento di stampa</span><span class="sxs-lookup"><span data-stu-id="b6c99-176">Define the action to be triggered by the On Press event</span></span>
6. <span data-ttu-id="b6c99-177">Configurare il cubo per la ricezione dell'evento on release</span><span class="sxs-lookup"><span data-stu-id="b6c99-177">Configure the cube to receive the On Release event</span></span>
7. <span data-ttu-id="b6c99-178">Definire l'azione che deve essere attivata dall'evento on release</span><span class="sxs-lookup"><span data-stu-id="b6c99-178">Define the action to be triggered by the On Release event</span></span>
8. <span data-ttu-id="b6c99-179">Testare il pulsante usando la simulazione in-Editor</span><span class="sxs-lookup"><span data-stu-id="b6c99-179">Test the button using the in-editor simulation</span></span>

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a><span data-ttu-id="b6c99-180">1. aggiungere un pulsante stampabile prefabbricato alla scena</span><span class="sxs-lookup"><span data-stu-id="b6c99-180">1. Add a pressable button prefab to the scene</span></span>

> [!TIP]
> <span data-ttu-id="b6c99-181">Una <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">preproduzione è una</a> GameObject preconfigurata archiviata come asset Unity e può essere riutilizzata in tutto il progetto.</span><span class="sxs-lookup"><span data-stu-id="b6c99-181">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="b6c99-182">Nella **finestra del progetto**cercare **PressableButtonHoloLens2** per individuare il prefabbricato che verrà usato per questo esempio:</span><span class="sxs-lookup"><span data-stu-id="b6c99-182">In the **Project window**, search for **PressableButtonHoloLens2** to locate the prefab you will use for this example:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

<span data-ttu-id="b6c99-184">Nei risultati della **ricerca** selezionare la prefabbricata **PressableButtonHoloLens2** e **trascinarla** nella finestra della **gerarchia** per aggiungerla alla scena:</span><span class="sxs-lookup"><span data-stu-id="b6c99-184">In the **Search** result, select the **PressableButtonHoloLens2** prefab and **drag** it into the **Hierarchy** window to add it to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="b6c99-186">Per visualizzare la scena come illustrato nell'immagine seguente, fare doppio clic sull'oggetto PressableButtonHoloLens2 nella finestra della gerarchia per attivarlo, quindi usare il <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Gizmo della scena</a>, situato nell'angolo superiore destro della finestra della scena, per regolare l'angolo di visualizzazione in modo che sia lungo l'asse Z successivo.</span><span class="sxs-lookup"><span data-stu-id="b6c99-186">To display your scene as shown in the image below, double-click the PressableButtonHoloLens2 object in the Hierarchy window to bring it into focus, then use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis.</span></span>

<span data-ttu-id="b6c99-187">Con l'oggetto **PressableButtonHoloLens2** ancora selezionato, nella finestra di **controllo** :</span><span class="sxs-lookup"><span data-stu-id="b6c99-187">With the **PressableButtonHoloLens2** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="b6c99-188">Modificare la **posizione** di trasformazione in modo che sia posizionata davanti alla fotocamera, posizionata in corrispondenza dell'origine, ad esempio x = 0, y = 0 e z = 0,5</span><span class="sxs-lookup"><span data-stu-id="b6c99-188">Change its Transform **Position** so it's positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="b6c99-190">In generale, 1 unità di posizione in Unity è approssimativamente equivalente a 1 metro nel mondo fisico.</span><span class="sxs-lookup"><span data-stu-id="b6c99-190">In general, 1 position unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="b6c99-191">Esistono tuttavia alcune eccezioni, ad esempio quando gli oggetti sono elementi figlio di oggetti ridimensionati.</span><span class="sxs-lookup"><span data-stu-id="b6c99-191">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span>

### <a name="2-add-a-cube-to-the-scene"></a><span data-ttu-id="b6c99-192">2. aggiungere un cubo alla scena</span><span class="sxs-lookup"><span data-stu-id="b6c99-192">2. Add a cube to the scene</span></span>

<span data-ttu-id="b6c99-193">Fare clic con il pulsante destro del mouse su un punto vuoto all'interno della finestra della gerarchia e selezionare **oggetto 3d** > **cubo** per aggiungere un cubo alla scena:</span><span class="sxs-lookup"><span data-stu-id="b6c99-193">Right-click on an empty spot inside the Hierarchy window and select **3D Object** > **Cube** to add a cube to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

<span data-ttu-id="b6c99-195">Con l'oggetto **cubo** ancora selezionato, nella finestra di **controllo** :</span><span class="sxs-lookup"><span data-stu-id="b6c99-195">With the **Cube** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="b6c99-196">Modificare la **posizione** di trasformazione in modo che sia posizionata vicino al pulsante stampabile, ma non sovrapposta, ad esempio x = 0, y = 0,04 e z = 0,5</span><span class="sxs-lookup"><span data-stu-id="b6c99-196">Change its Transform **Position** so its located near the pressable button, but not overlapping with it, for example, x = 0, y = 0.04, and z = 0.5</span></span>
* <span data-ttu-id="b6c99-197">Modificare la **scala** di trasformazione in base alle dimensioni appropriate, ad esempio x = 0,02, y = 0,02 e z = 0,02</span><span class="sxs-lookup"><span data-stu-id="b6c99-197">Change its Transform **Scale** to a suitable size, for example, x = 0.02, y = 0.02, and z = 0.02</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a><span data-ttu-id="b6c99-199">3. configurare il tipo di evento InteractableOnPressReceiver</span><span class="sxs-lookup"><span data-stu-id="b6c99-199">3. Configure the InteractableOnPressReceiver event type</span></span>

<span data-ttu-id="b6c99-200">Nella finestra gerarchia selezionare l'oggetto **PressableButtonHoloLens2** , quindi nel **menu hamburger**della finestra di **controllo** Selezionare **Comprimi tutti i componenti** per ottenere una panoramica di tutti i componenti in questo oggetto:</span><span class="sxs-lookup"><span data-stu-id="b6c99-200">In the Hierarchy window, select the **PressableButtonHoloLens2** object, then in the **Inspector** window **hamburger menu**, select **Collapse All Components** to get an overview of all components on this object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

<span data-ttu-id="b6c99-202">Espandere il componente **interactable (script)** , quindi individuare ed espandere la sezione **eventi** > **ricevitori** :</span><span class="sxs-lookup"><span data-stu-id="b6c99-202">Expand the **Interactable (Script)** component, then locate and expand the **Events** > **Receivers** section:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

<span data-ttu-id="b6c99-204">Fare clic sul pulsante **Aggiungi evento** per creare un nuovo ricevitore di eventi di tipo **InteractableOnPressReceiver**:</span><span class="sxs-lookup"><span data-stu-id="b6c99-204">Click the **Add Event** button, to create a new event receiver of Event Receiver Type **InteractableOnPressReceiver**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> <span data-ttu-id="b6c99-206">Il tipo di ricevitore di eventi denominato InteractableOnPressReceiver consente al pulsante di rispondere a un evento premuto quando una mano rilevata preme il pulsante.</span><span class="sxs-lookup"><span data-stu-id="b6c99-206">The Event Receiver Type named InteractableOnPressReceiver allows the button to respond to a pressed event when a tracked hand presses the button.</span></span>

<span data-ttu-id="b6c99-207">Per il ricevitore di eventi appena creato, modificare il **filtro interazione** in **near e lontano**:</span><span class="sxs-lookup"><span data-stu-id="b6c99-207">For the newly created event receiver, change the **Interaction Filter** to **Near and Far**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a><span data-ttu-id="b6c99-209">4. configurare il cubo per la ricezione dell'evento di stampa</span><span class="sxs-lookup"><span data-stu-id="b6c99-209">4. Configure the cube to receive the On Press event</span></span>

<span data-ttu-id="b6c99-210">Dalla finestra gerarchia, **fare clic e trascinare** il **cubo** nel campo oggetto **Proprietà evento** per l'evento **on Press ()** per assegnare il cubo come ricevitore dell'evento on Press ():</span><span class="sxs-lookup"><span data-stu-id="b6c99-210">From the Hierarchy window, **click-and-drag** the **Cube** into the **Event Properties** object field for the **On Press ()** event to assign the Cube as a receiver of the On Press () event:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a><span data-ttu-id="b6c99-212">5. definire l'azione che deve essere attivata dall'evento di stampa</span><span class="sxs-lookup"><span data-stu-id="b6c99-212">5. Define the action to be triggered by the On Press event</span></span>

<span data-ttu-id="b6c99-213">Fare clic sull'elenco a discesa azione, attualmente assegnata **Nessuna funzione**e selezionare **MeshRenderer** \*\* > Material Material per\*\* impostare la proprietà Material del cubo da modificare quando viene attivato l'evento on Press ():</span><span class="sxs-lookup"><span data-stu-id="b6c99-213">Click the action dropdown, currently assigned **No Function**, and select **MeshRenderer** > **Material material** to set the Cube's material property to be changed when the On Press () event is triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

<span data-ttu-id="b6c99-215">Fare clic sull'icona del **cerchio** piccolo accanto al campo Material, attualmente popolata con **None (Material)** , per aprire la finestra Seleziona materiale:</span><span class="sxs-lookup"><span data-stu-id="b6c99-215">Click the small **circle** icon next to the material field, currently populated with **None (Material)**, to open the Select Material window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

<span data-ttu-id="b6c99-217">Nella finestra Seleziona materiale **cercare** **MRTK_Standard** e selezionare un materiale appropriato, ad esempio **MRTK_Standard_Cyan** in modo che il colore del cubo venga modificato in ciano quando si preme il pulsante:</span><span class="sxs-lookup"><span data-stu-id="b6c99-217">In the Select Material window, **search** for **MRTK_Standard** and select a suitable material, for example, **MRTK_Standard_Cyan** so the Cube's color changes to cyan when the button is pressed:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a><span data-ttu-id="b6c99-219">6. configurare il cubo per la ricezione dell'evento on release</span><span class="sxs-lookup"><span data-stu-id="b6c99-219">6. Configure the cube to receive the On Release event</span></span>

<span data-ttu-id="b6c99-220">**Ripeti** Passaggio 4 per l'evento on release per assegnare il **cubo** come ricevitore dell'evento **on release ()** .</span><span class="sxs-lookup"><span data-stu-id="b6c99-220">**Repeat** Step 4 for the On Release event to assign the **Cube** as a receiver of the **On Release ()** event.</span></span>

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a><span data-ttu-id="b6c99-221">7. definire l'azione che deve essere attivata dall'evento on release</span><span class="sxs-lookup"><span data-stu-id="b6c99-221">7. Define the action to be triggered by the On Release event</span></span>

<span data-ttu-id="b6c99-222">**Ripeti** Passaggio 5 per l'evento on release, ma scegliere il materiale **MRTK_Standard_LightGray** in modo che il colore del cubo torni al colore grigio chiaro originale quando viene rilasciato il pulsante:</span><span class="sxs-lookup"><span data-stu-id="b6c99-222">**Repeat** Step 5 for the On Release event, but choose the **MRTK_Standard_LightGray** material so the Cube's color returns to its original light gray color when the button is released:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a><span data-ttu-id="b6c99-224">8. testare il pulsante usando la simulazione in-Editor</span><span class="sxs-lookup"><span data-stu-id="b6c99-224">8. Test the button using the in-editor simulation</span></span>

<span data-ttu-id="b6c99-225">Premere il pulsante **Play (Riproduci** ) per attivare la modalità di gioco e usare la simulazione di input nell'editor per testare il pulsante appena configurato.</span><span class="sxs-lookup"><span data-stu-id="b6c99-225">Press the **Play** button to enter Game mode and use the in-editor input simulation to test your newly configured button.</span></span>

<span data-ttu-id="b6c99-226">Pulsante non premuto (barra spaziatrice + rotellina di scorrimento del mouse indietro):</span><span class="sxs-lookup"><span data-stu-id="b6c99-226">Button not pressed (spacebar + mouse scroll wheel backward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

<span data-ttu-id="b6c99-228">Pulsante premuto (barra spaziatrice + rotellina di scorrimento del mouse avanti):</span><span class="sxs-lookup"><span data-stu-id="b6c99-228">Button pressed (spacebar + mouse scroll wheel forward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> <span data-ttu-id="b6c99-230">Per informazioni su come usare la simulazione di input nell'editor, è possibile fare riferimento all'uso [della simulazione di input manuale in-Editor per testare una](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) Guida alla scena nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="b6c99-230">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="b6c99-231">Creazione di un pannello di pulsanti con la raccolta di oggetti griglia di MRTK</span><span class="sxs-lookup"><span data-stu-id="b6c99-231">Creating a panel of buttons using MRTK’s Grid Object Collection</span></span>

<span data-ttu-id="b6c99-232">In questa sezione si apprenderà come allineare automaticamente più pulsanti in un'interfaccia utente accurata usando lo strumento di raccolta oggetti Grid di MRTK.</span><span class="sxs-lookup"><span data-stu-id="b6c99-232">In this section, you will learn how to automatically align multiple buttons into a neat user interface by using the MRTK’s Grid Object Collection tool.</span></span>

<span data-ttu-id="b6c99-233">In questo particolare esempio viene illustrato come creare un pannello con cinque pulsanti allineati orizzontalmente.</span><span class="sxs-lookup"><span data-stu-id="b6c99-233">This particular example will show you how to a create a panel with five buttons aligned horizontally.</span></span> <span data-ttu-id="b6c99-234">Tuttavia, è possibile seguire questi stessi principi per creare altri layout.</span><span class="sxs-lookup"><span data-stu-id="b6c99-234">However, you may follow these same principles to create other layouts.</span></span>

<span data-ttu-id="b6c99-235">Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:</span><span class="sxs-lookup"><span data-stu-id="b6c99-235">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="b6c99-236">Padre degli oggetti Button in un oggetto padre</span><span class="sxs-lookup"><span data-stu-id="b6c99-236">Parent the button objects to a parent object</span></span>
2. <span data-ttu-id="b6c99-237">Aggiungere e configurare il componente Grid Object Collection (script)</span><span class="sxs-lookup"><span data-stu-id="b6c99-237">Add and configure the Grid Object Collection (Script) component</span></span>
3. <span data-ttu-id="b6c99-238">Testare i pulsanti usando la simulazione in-Editor</span><span class="sxs-lookup"><span data-stu-id="b6c99-238">Test the buttons using the in-editor simulation</span></span>

### <a name="1-parent-the-button-objects-to-a-parent-object"></a><span data-ttu-id="b6c99-239">1. padre degli oggetti Button in un oggetto padre</span><span class="sxs-lookup"><span data-stu-id="b6c99-239">1. Parent the button objects to a parent object</span></span>

<span data-ttu-id="b6c99-240">Fare clic con il pulsante destro del mouse su un punto vuoto all'interno della finestra della gerarchia e selezionare **Crea vuoto**:</span><span class="sxs-lookup"><span data-stu-id="b6c99-240">Right-click on an empty spot inside the Hierarchy window and select **Create Empty**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

<span data-ttu-id="b6c99-242">Fare clic con il pulsante destro del mouse sull'oggetto appena creato, scegliere **Rinomina**e assegnare un nome appropriato, ad esempio **buttoncollection**:</span><span class="sxs-lookup"><span data-stu-id="b6c99-242">Right-click on the newly created object, select **Rename**, and give it a suitable name, for example, **ButtonCollection**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

<span data-ttu-id="b6c99-244">Selezionare l'oggetto **PressableButtonHoloLens2** e **trascinarlo** sopra l'oggetto **buttoncollection** per impostarlo come figlio dell'oggetto buttoncollection:</span><span class="sxs-lookup"><span data-stu-id="b6c99-244">Select the **PressableButtonHoloLens2** object and **drag** it on top of the **ButtonCollection** object to make it a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

<span data-ttu-id="b6c99-246">Fare clic con il pulsante destro del mouse sull'oggetto **PressableButtonHoloLens2** e selezionare **duplicato** per crearne una copia:</span><span class="sxs-lookup"><span data-stu-id="b6c99-246">Right-click the **PressableButtonHoloLens2** object and select **Duplicate** to create a copy of it:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

<span data-ttu-id="b6c99-248">**Ripetere** questo passaggio quattro volte fino a quando non si dispone di un totale di cinque oggetti PressableButtonHoloLens2.</span><span class="sxs-lookup"><span data-stu-id="b6c99-248">**Repeat** this step four more times until you have a total of five PressableButtonHoloLens2 objects.</span></span>

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="b6c99-249">2. aggiungere e configurare il componente Grid Object Collection (script)</span><span class="sxs-lookup"><span data-stu-id="b6c99-249">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="b6c99-250">Con l'oggetto Buttoncollection selezionato nella finestra gerarchia, nella finestra di controllo fare clic sul pulsante **Add Component** , quindi cercare e selezionare **Grid Object Collection** per aggiungere un componente Grid Object Collection (script) all'oggetto buttoncollection:</span><span class="sxs-lookup"><span data-stu-id="b6c99-250">With the ButtonCollection object selected in the Hierarchy window, in the Inspector window, click the **Add Component** button, then search for and select **Grid Object Collection** to add a Grid Object Collection (Script) component to the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

<span data-ttu-id="b6c99-252">Configurare la raccolta di oggetti Grid (script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="b6c99-252">Configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="b6c99-253">Modificare **num Rows** su 1 in modo che tutti i pulsanti siano allineati in una singola riga</span><span class="sxs-lookup"><span data-stu-id="b6c99-253">Change **Num Rows** to 1 to have all buttons aligned on one single row</span></span>
* <span data-ttu-id="b6c99-254">Modificare la **larghezza della cella** a 0,05 per spaziare i pulsanti all'interno della riga</span><span class="sxs-lookup"><span data-stu-id="b6c99-254">Change **Cell Width** to 0.05 to space out the buttons within the row</span></span>

<span data-ttu-id="b6c99-255">Quindi fare clic sul pulsante **Aggiorna raccolta** per applicare la nuova configurazione:</span><span class="sxs-lookup"><span data-stu-id="b6c99-255">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> <span data-ttu-id="b6c99-257">Le modifiche di configurazione appena applicate rappresentano le modifiche minime necessarie per raggiungere l'obiettivo di posizionare i pulsanti in una singola riga.</span><span class="sxs-lookup"><span data-stu-id="b6c99-257">The configuration changes you just applied represent the minimum changes required to achieve the objective of placing the buttons in a single row.</span></span> <span data-ttu-id="b6c99-258">Tuttavia, nei progetti futuri, a seconda di fattori quali, ad esempio, l'orientamento degli oggetti padre e figlio, potrebbe essere necessario modificare altre impostazioni, ad esempio il tipo Orient.</span><span class="sxs-lookup"><span data-stu-id="b6c99-258">However, in future projects, depending on factors such as, for example, the orientation of the parent and child objects, you might need to adjust other settings such as, for example, the Orient Type.</span></span> <span data-ttu-id="b6c99-259">Per ulteriori informazioni sulla raccolta di oggetti Grid di MRTK, è possibile visitare la guida relativa agli [script della raccolta di oggetti](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) nel portale della documentazione di [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="b6c99-259">To learn more about MRTK's Grid Object Collection, you can visit the [Object collection scripts](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

<span data-ttu-id="b6c99-260">Con l'oggetto Buttoncollection ancora selezionato nella finestra gerarchia, nella finestra Inspector modificare la **posizione** di trasformazione dell'oggetto buttoncollection in modo che gli oggetti pulsante figlio siano posizionati davanti alla fotocamera, posizionata in corrispondenza dell'origine, ad esempio x = 0, y = 0 e z = 0,5:</span><span class="sxs-lookup"><span data-stu-id="b6c99-260">With the ButtonCollection object still selected in the Hierarchy window, in the Inspector window, change the ButtonCollection object's Transform **Position** so its child button objects are positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> <span data-ttu-id="b6c99-262">Quando è stato aggiunto per la prima volta la prefabbricazione PressableButtonHoloLens2 alla scena nella sezione [movimenti di rilevamento mano e pulsanti interactabili](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) , è stata posizionata davanti alla fotocamera.</span><span class="sxs-lookup"><span data-stu-id="b6c99-262">When you first added the PressableButtonHoloLens2 prefab to the scene in the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) section above, you positioned it in front of the camera.</span></span> <span data-ttu-id="b6c99-263">Tuttavia, poiché la raccolta di oggetti Grid controlla la posizione immediata degli oggetti figlio, la posizione Z degli oggetti figlio PressableButtonHoloLens2 è stata reimpostata su 0 in base alla distanza predefinita della raccolta di oggetti Grid rispetto al valore padre 0.</span><span class="sxs-lookup"><span data-stu-id="b6c99-263">However, because the Grid Object Collection controls its immediate child objects' position, the PressableButtonHoloLens2 child objects' Z Position were reset to 0 according to the Grid Object Collection's default Distance from parent value of 0.</span></span> <span data-ttu-id="b6c99-264">In questo modo, per evitare che la relazione posizionale padre/figlio sia organizzata, è il motivo per cui è stata spostata in avanti la posizione dell'oggetto Buttoncollection padre anziché configurare la distanza dal valore padre per spostare in avanti gli oggetti figlio PressableButtonHoloLens2.</span><span class="sxs-lookup"><span data-stu-id="b6c99-264">This, and to keep the parent/child positional relationship organized, is why we moved the parent ButtonCollection object's position forward instead of configuring the Distance from parent value to move the PressableButtonHoloLens2 child objects forward.</span></span>

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a><span data-ttu-id="b6c99-265">3. testare i pulsanti usando la simulazione in-Editor</span><span class="sxs-lookup"><span data-stu-id="b6c99-265">3. Test the buttons using the in-editor simulation</span></span>

<span data-ttu-id="b6c99-266">Premere il pulsante Play (Riproduci) per attivare la modalità di gioco e usare la simulazione di input nell'editor per testare ogni pulsante in nel pannello dei pulsanti appena creato:</span><span class="sxs-lookup"><span data-stu-id="b6c99-266">Press the Play button to enter Game mode and use the in-editor input simulation to test each of the buttons in in your newly created panel of buttons:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> <span data-ttu-id="b6c99-268">Attualmente, quando si preme uno dei cinque pulsanti, il colore del cubo diventa ciano.</span><span class="sxs-lookup"><span data-stu-id="b6c99-268">Currently, when your press any of the five buttons, the cube color changes to cyan.</span></span> <span data-ttu-id="b6c99-269">Per rendere più interessante l'esperienza, utilizzare le informazioni appena apprese per configurare ogni pulsante per modificare il cubo in un colore diverso.</span><span class="sxs-lookup"><span data-stu-id="b6c99-269">To make the experience more interesting, use what you just learn to configure each button to change the cube to a different color.</span></span>

## <a name="adding-text-into-your-scene"></a><span data-ttu-id="b6c99-270">Aggiunta di testo alla scena</span><span class="sxs-lookup"><span data-stu-id="b6c99-270">Adding text into your scene</span></span>

<span data-ttu-id="b6c99-271">In questa sezione si apprenderà come aggiungere testo alle esperienze di realtà mista usando TextMesh Pro di Unity, preparato nella sezione [Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) dell'esercitazione precedente.</span><span class="sxs-lookup"><span data-stu-id="b6c99-271">In this section, you will learn how to add text to your mixed reality experiences using Unity's TextMesh Pro, which you prepared in the [Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) section of the previous tutorial.</span></span>

<span data-ttu-id="b6c99-272">In questo particolare esempio verrà aggiunta un'etichetta semplice sotto la raccolta di pulsanti creata nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="b6c99-272">In this particular example, you will add a simple label underneath the button collection you created in the previous section.</span></span>

<span data-ttu-id="b6c99-273">Fare clic con il pulsante destro del mouse sull'oggetto Buttoncollection e selezionare **oggetto 3d** > **Text-TextMeshPro** per creare un oggetto TextMeshPro come figlio dell'oggetto buttoncollection:</span><span class="sxs-lookup"><span data-stu-id="b6c99-273">Right-click on the ButtonCollection object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro object as a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

<span data-ttu-id="b6c99-275">Con l'oggetto TextMeshPro appena creato, denominato testo (TMP), ancora selezionato, nella finestra di controllo modificare la posizione e le dimensioni in modo che l'etichetta venga posizionata perfettamente sotto la raccolta dei pulsanti, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="b6c99-275">With the newly created TextMeshPro object, named Text (TMP), still selected, in the Inspector window change its position and size so the label is placed neatly underneath the button collection, for example:</span></span>

* <span data-ttu-id="b6c99-276">Modificare la trasformazione Rect **pos Y** in-0,0425</span><span class="sxs-lookup"><span data-stu-id="b6c99-276">Change the Rect Transform **Pos Y** to -0.0425</span></span>
* <span data-ttu-id="b6c99-277">Modificare la **larghezza** della trasformazione Rect in 0,24</span><span class="sxs-lookup"><span data-stu-id="b6c99-277">Change the Rect Transform **Width** to 0.24</span></span>
* <span data-ttu-id="b6c99-278">Modificare l' **altezza** di trasformazione Rect in 0,024</span><span class="sxs-lookup"><span data-stu-id="b6c99-278">Change the Rect Transform **Height** to 0.024</span></span>

<span data-ttu-id="b6c99-279">Aggiornare quindi il testo in base a cui si riferisce l'etichetta e scegliere le proprietà del tipo di carattere, in modo che il testo entri nell'etichetta, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="b6c99-279">Then update the text to reflect what the label is for and choose font properties so the text fits within the label, for example:</span></span>

* <span data-ttu-id="b6c99-280">Modificare il **testo** della funzionalità text mesh Pro (script) in un insieme di pulsanti</span><span class="sxs-lookup"><span data-stu-id="b6c99-280">Change the Text Mesh Pro (Script) **Text** to Button Collection</span></span>
* <span data-ttu-id="b6c99-281">Modificare lo **stile del tipo di carattere** text mesh Pro (script) in grassetto</span><span class="sxs-lookup"><span data-stu-id="b6c99-281">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="b6c99-282">Modificare le **dimensioni del tipo di carattere** text mesh Pro (script) in 0,2</span><span class="sxs-lookup"><span data-stu-id="b6c99-282">Change the Text Mesh Pro (Script) **Font Size** to 0.2</span></span>
* <span data-ttu-id="b6c99-283">Modificare l' **allineamento** di Text mesh Pro (script) in centro e al centro</span><span class="sxs-lookup"><span data-stu-id="b6c99-283">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="b6c99-285">Complimenti</span><span class="sxs-lookup"><span data-stu-id="b6c99-285">Congratulations</span></span>

<span data-ttu-id="b6c99-286">In questa esercitazione si è appreso come clonare, personalizzare e configurare un'impostazione del profilo MRTK.</span><span class="sxs-lookup"><span data-stu-id="b6c99-286">In this tutorial, you learned how to clone, customize, and configure an MRTK profile setting.</span></span> <span data-ttu-id="b6c99-287">Si è inoltre appreso come interagire con i pulsanti per attivare eventi usando le mani rilevate in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b6c99-287">You also learned how to interact with buttons to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="b6c99-288">Infine, si è appreso come creare una semplice interfaccia dell'interfaccia utente usando il componente della raccolta di oggetti Grid di MRTK e il testo di Unity mesh Pro.</span><span class="sxs-lookup"><span data-stu-id="b6c99-288">Finally, you learned how to create a simple UI interface using the MRTK's Grid Object Collection component and Unity's Text Mesh Pro.</span></span>

[<span data-ttu-id="b6c99-289">Esercitazione successiva: 4. posizionamento del contenuto dinamico e uso dei risolutori</span><span class="sxs-lookup"><span data-stu-id="b6c99-289">Next Tutorial: 4. Placing dynamic content and using solvers</span></span>](mrlearning-base-ch3.md)

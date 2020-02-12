---
title: Esercitazioni introduttive-7. Creazione di un'applicazione di esempio del modulo Lunar
description: In questa lezione vengono combinati più concetti appresi dalle lezioni precedenti per creare un'esperienza di esempio univoca.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: b5b1bd0115822449bd6098f78cfc94d909169737
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129451"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="eec6f-105">7. creazione di un'applicazione di esempio del modulo Lunar</span><span class="sxs-lookup"><span data-stu-id="eec6f-105">7. Creating a Lunar Module sample application</span></span>
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

<span data-ttu-id="eec6f-106">In questa esercitazione vengono combinati più concetti rispetto alle lezioni precedenti per creare un'esperienza di esempio univoca.</span><span class="sxs-lookup"><span data-stu-id="eec6f-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="eec6f-107">Si apprenderà come creare un'applicazione di assembly di parti in base alla quale un utente deve usare le mani registrate per scegliere le parti e provare a assemblare un modulo lunare.</span><span class="sxs-lookup"><span data-stu-id="eec6f-107">You will learn how to create a part assembly application whereby a user needs to use tracked hands to pick up parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="eec6f-108">Si utilizzeranno pulsanti stampabili per attivare e disattivare gli hint di posizionamento, per reimpostare l'esperienza e per avviare il modulo Lunar nello spazio.</span><span class="sxs-lookup"><span data-stu-id="eec6f-108">You will use pressable buttons to toggle placement hints on and off, to reset the experience, and to launch the lunar module into space!</span></span>

<span data-ttu-id="eec6f-109">Nelle esercitazioni future si continuerà a sviluppare questa esperienza, che include potenti casi d'uso multiutente che sfruttano gli ancoraggi spaziali di Azure per l'allineamento spaziale.</span><span class="sxs-lookup"><span data-stu-id="eec6f-109">In future tutorials, you will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="eec6f-110">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="eec6f-110">Objectives</span></span>

* <span data-ttu-id="eec6f-111">Combinare i vari concetti illustrati nelle lezioni precedenti per creare un'esperienza unica</span><span class="sxs-lookup"><span data-stu-id="eec6f-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
* <span data-ttu-id="eec6f-112">Apprendere come attivare o disattivare gli oggetti</span><span class="sxs-lookup"><span data-stu-id="eec6f-112">Learn how to toggle objects</span></span>
* <span data-ttu-id="eec6f-113">Attivare eventi complessi usando i pulsanti a pressione</span><span class="sxs-lookup"><span data-stu-id="eec6f-113">Trigger complex events using pressable buttons</span></span>
* <span data-ttu-id="eec6f-114">Usare la forza e la fisica dei corpi rigidi</span><span class="sxs-lookup"><span data-stu-id="eec6f-114">Use rigidbody physics and forces</span></span>
* <span data-ttu-id="eec6f-115">Esplorare l'uso delle descrizioni comandi</span><span class="sxs-lookup"><span data-stu-id="eec6f-115">Explore the use of tool tips</span></span>

## <a name="lunar-module-parts-overview"></a><span data-ttu-id="eec6f-116">Cenni preliminari sulle parti del modulo Lunar</span><span class="sxs-lookup"><span data-stu-id="eec6f-116">Lunar Module Parts overview</span></span>
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

<span data-ttu-id="eec6f-117">In questa sezione si creerà un semplice problema di assembly di parti in cui l'obiettivo dell'utente è inserire cinque parti distribuite nella tabella nella posizione corretta nel modulo Lunar.</span><span class="sxs-lookup"><span data-stu-id="eec6f-117">In this section, you will create a simple part assembly challenge where the user's goal is to place five parts that are spread out on the table at the correct location on the Lunar Module.</span></span>

<span data-ttu-id="eec6f-118">Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:</span><span class="sxs-lookup"><span data-stu-id="eec6f-118">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="eec6f-119">Aggiungere la prefabbricazione di lanciarazzi alla scena</span><span class="sxs-lookup"><span data-stu-id="eec6f-119">Add the Rocket Launcher prefab to the scene</span></span>
2. <span data-ttu-id="eec6f-120">Abilitare la manipolazione degli oggetti per tutte le parti</span><span class="sxs-lookup"><span data-stu-id="eec6f-120">Enable object manipulation for all the parts</span></span>
3. <span data-ttu-id="eec6f-121">Aggiungere e configurare il componente Demo assembly parti (script)</span><span class="sxs-lookup"><span data-stu-id="eec6f-121">Add and configure the Part Assembly Demo (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="eec6f-122">Il componente Demo assembly parti (script) non fa parte di MRTK.</span><span class="sxs-lookup"><span data-stu-id="eec6f-122">The Part Assembly Demo (Script) component is not part of MRTK.</span></span> <span data-ttu-id="eec6f-123">È stato fornito con le risorse dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="eec6f-123">It was provided with this tutorial's assets.</span></span>

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a><span data-ttu-id="eec6f-124">1. aggiungere la prefabbricazione di lanciarazzi alla scena</span><span class="sxs-lookup"><span data-stu-id="eec6f-124">1. Add the Rocket Launcher prefab to the scene</span></span>

<span data-ttu-id="eec6f-125">Nella finestra del progetto passare al **asset** > **MRTK. Esercitazioni. GettingStarted** > **prefabbricati** > cartella **RocketLauncher** , trascinare il prefabbricato **RocketLauncher** nella finestra gerarchia per aggiungerlo alla scena e quindi posizionarlo in una posizione appropriata, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="eec6f-125">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher** prefab into the Hierarchy window to add it to your scene, and then position it at a suitable location, for example:</span></span>

* <span data-ttu-id="eec6f-126">Posizione di trasformazione X = 1,5, Y =-0,4, Z = 0, in modo che venga posizionata a destra dell'utente all'altezza della vita</span><span class="sxs-lookup"><span data-stu-id="eec6f-126">Transform Position X = 1.5, Y = -0.4, Z = 0, so it is positioned to the right of the user at waist height</span></span>
* <span data-ttu-id="eec6f-127">Rotazione della trasformazione X = 0, Y = 180, Z = 0, quindi le funzionalità principali dell'esperienza sono relative all'utente</span><span class="sxs-lookup"><span data-stu-id="eec6f-127">Transform Rotation X = 0, Y = 180, Z = 0, so the main features of the experience faces the user</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a><span data-ttu-id="eec6f-129">2. abilitare la manipolazione degli oggetti per tutte le parti</span><span class="sxs-lookup"><span data-stu-id="eec6f-129">2. Enable object manipulation for all the parts</span></span>

<span data-ttu-id="eec6f-130">Nella finestra gerarchia individuare l'oggetto RocketLauncher > **LunarModuleParts** e selezionare tutti gli **oggetti figlio**, aggiungere il componente **gestione manipolazione (script)** e il componente **near Interaction (script** ), quindi configurare il gestore di manipolazione (script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="eec6f-130">In the Hierarchy window, locate the RocketLauncher > **LunarModuleParts** object and select all the **child objects**, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="eec6f-131">Modificare il **tipo di manipolazione a due passi** per spostare la rotazione in modo che la scalabilità sia disabilitata</span><span class="sxs-lookup"><span data-stu-id="eec6f-131">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>
* <span data-ttu-id="eec6f-132">Deselezionare la casella di controllo **Consenti modifiche a distanza** per consentire solo l'interazione near</span><span class="sxs-lookup"><span data-stu-id="eec6f-132">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="eec6f-134">Per un promemoria, con le istruzioni dettagliate su come implementare la manipolazione degli oggetti, è possibile fare riferimento alle istruzioni di [manipolazione degli oggetti 3D](mrlearning-base-ch4.md#manipulating-3d-objects) .</span><span class="sxs-lookup"><span data-stu-id="eec6f-134">For a reminder, with step by step instructions, on how to implement object manipulation, you can refer to the [Manipulating 3D Objects](mrlearning-base-ch4.md#manipulating-3d-objects) instructions.</span></span>

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a><span data-ttu-id="eec6f-135">3. aggiungere e configurare il componente Demo assembly parte (script)</span><span class="sxs-lookup"><span data-stu-id="eec6f-135">3. Add and configure the Part Assembly Demo (Script) component</span></span>

<span data-ttu-id="eec6f-136">Con tutti gli oggetti figlio LunarModuleParts ancora selezionati, aggiungere un componente di **origine audio** , quindi configurarlo come segue:</span><span class="sxs-lookup"><span data-stu-id="eec6f-136">With all the LunarModuleParts child objects still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="eec6f-137">Assegnare un clip audio adatto al campo **AudioClip** , ad esempio MRKT_Scale_Start</span><span class="sxs-lookup"><span data-stu-id="eec6f-137">Assign a suitable audio clip to the **AudioClip** field, for example, MRKT_Scale_Start</span></span>
* <span data-ttu-id="eec6f-138">Deselezionare la casella di controllo **Riproduci in** modo non attivo, quindi il clip audio non viene riprodotto automaticamente quando viene caricata la scena</span><span class="sxs-lookup"><span data-stu-id="eec6f-138">Un-check the **Play On Awake** checkbox, so the audio clip does not automatically play when the scene loads</span></span>
* <span data-ttu-id="eec6f-139">Modificare **Blend spaziale** su 1 per abilitare l'audio spaziale</span><span class="sxs-lookup"><span data-stu-id="eec6f-139">Change **Spatial Blend** to 1, to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

<span data-ttu-id="eec6f-141">Con tutti gli oggetti figlio LunarModuleParts ancora selezionati, aggiungere il componente **demo assembly parti (script)** :</span><span class="sxs-lookup"><span data-stu-id="eec6f-141">With all the LunarModuleParts child objects still selected, add the **Part Assembly Demo  (Script)** component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

<span data-ttu-id="eec6f-143">Nella finestra gerarchia selezionare l'oggetto **RoverEnclosure** e configurare il componente **demo assembly parte (script)** come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="eec6f-143">In the Hierarchy window, select the **RoverEnclosure** object and configure its **Part Assembly Demo (Script)** component as follows:</span></span>

* <span data-ttu-id="eec6f-144">All'oggetto **da inserire** nel campo, assegnare l'oggetto stesso, in questo caso l'oggetto **RoverEnclosure**</span><span class="sxs-lookup"><span data-stu-id="eec6f-144">To the **Object To Place** field, assign the object itself, in this case, the **RoverEnclosure** object</span></span>
* <span data-ttu-id="eec6f-145">Per il campo **percorso da inserire** , assegnare l'oggetto PlacementHints corrispondente, in questo caso l'oggetto **RoverEnclosure_PlacementHints**</span><span class="sxs-lookup"><span data-stu-id="eec6f-145">To the **Location To Place** field, assign the corresponding PlacementHints object, in this case, the **RoverEnclosure_PlacementHints** object</span></span>
* <span data-ttu-id="eec6f-146">Al campo **oggetto descrizione** comando assegnare il ToolTipObject corrispondente, in questo caso l'oggetto **RoverEnclosure_ToolTip**</span><span class="sxs-lookup"><span data-stu-id="eec6f-146">To the **Tool Tip Object** field, assign the corresponding ToolTipObject, in this case, the **RoverEnclosure_ToolTip** object</span></span>
* <span data-ttu-id="eec6f-147">Nel campo **origine audio** assegnare l'oggetto stesso, in questo caso l'oggetto **RoverEnclosure**</span><span class="sxs-lookup"><span data-stu-id="eec6f-147">To the **Audio Source** field, assign the object itself, in this case, the **RoverEnclosure** object</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

<span data-ttu-id="eec6f-149">**Ripetere** per ognuno degli altri oggetti figlio LunarModuleParts, ad esempio serbatoio, EnergyCell, DockingPortal e ExternalSensor.</span><span class="sxs-lookup"><span data-stu-id="eec6f-149">**Repeat** for each of the other LunarModuleParts child objects, i.e. FuelTank, EnergyCell, DockingPortal, and ExternalSensor.</span></span>

<span data-ttu-id="eec6f-150">Se a questo punto si immette la modalità di gioco e si sposta un'oggetto per posizionarlo ' vicino alla posizione corrispondente, si noterà quanto segue:</span><span class="sxs-lookup"><span data-stu-id="eec6f-150">If you now enter Game mode and move an 'Object To Place' close to it's corresponding 'Location To Place' you will notice:</span></span>

* <span data-ttu-id="eec6f-151">L'oggetto verrà inserito e associato all'oggetto LunarModule in modo che diventi parte del modulo Lunar</span><span class="sxs-lookup"><span data-stu-id="eec6f-151">The object will snap into place and be parented under the LunarModule object so it becomes part of the Lunar Module</span></span>
* <span data-ttu-id="eec6f-152">L'origine audio nell'oggetto riprodurrà il clip audio assegnato in corrispondenza della posizione dell'oggetto</span><span class="sxs-lookup"><span data-stu-id="eec6f-152">The Audio Source on the object will play the assigned Audio Clip at the location of the object</span></span>
* <span data-ttu-id="eec6f-153">L'oggetto descrizione comando corrispondente verrà nascosto</span><span class="sxs-lookup"><span data-stu-id="eec6f-153">The corresponding Tool Tip object will be hidden</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> <span data-ttu-id="eec6f-155">Per un promemoria su come usare la simulazione di input nell'editor, è possibile fare riferimento a [usando la simulazione di input manuale in-Editor per testare una](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) Guida alla scena nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="eec6f-155">For a reminder on how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="configuring-the-lunar-module"></a><span data-ttu-id="eec6f-156">Configurazione del modulo lunare</span><span class="sxs-lookup"><span data-stu-id="eec6f-156">Configuring the Lunar Module</span></span>

<span data-ttu-id="eec6f-157">In questa sezione si aggiungeranno altre funzionalità all'applicazione di avvio Rocket in modo che l'utente possa:</span><span class="sxs-lookup"><span data-stu-id="eec6f-157">In this section, you will add additional features to the Rocket Launcher application so the user can:</span></span>

* <span data-ttu-id="eec6f-158">Interagire con il modulo Lunar</span><span class="sxs-lookup"><span data-stu-id="eec6f-158">Interact with the Lunar Module</span></span>
* <span data-ttu-id="eec6f-159">Avviare il modulo Lunar nello spazio e riprodurre un suono quando viene avviato</span><span class="sxs-lookup"><span data-stu-id="eec6f-159">Launch the Lunar Module into space and play a sound when it is launched</span></span>
* <span data-ttu-id="eec6f-160">Reimpostare l'applicazione in modo che il modulo Lunar e tutte le parti vengano riposizionati nella posizione originale</span><span class="sxs-lookup"><span data-stu-id="eec6f-160">Reset the application so the Lunar Module and all the part are placed back to their original position</span></span>
* <span data-ttu-id="eec6f-161">Nascondere gli hint di selezione host per rendere più difficile la verifica dell'assembly della parte.</span><span class="sxs-lookup"><span data-stu-id="eec6f-161">Hide the placement hints to make the part assembly challenge more difficult.</span></span>

<span data-ttu-id="eec6f-162">Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:</span><span class="sxs-lookup"><span data-stu-id="eec6f-162">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="eec6f-163">Abilita manipolazione oggetti</span><span class="sxs-lookup"><span data-stu-id="eec6f-163">Enable object manipulation</span></span>
2. <span data-ttu-id="eec6f-164">Abilita fisica</span><span class="sxs-lookup"><span data-stu-id="eec6f-164">Enable physics</span></span>
3. <span data-ttu-id="eec6f-165">Aggiungere un componente di origine audio</span><span class="sxs-lookup"><span data-stu-id="eec6f-165">Add an Audio Source component</span></span>
4. <span data-ttu-id="eec6f-166">Aggiungere e configurare il componente Launch Lunar Module (script)</span><span class="sxs-lookup"><span data-stu-id="eec6f-166">Add and configure the Launch Lunar Module (Script) component</span></span>
5. <span data-ttu-id="eec6f-167">Aggiungere e configurare il componente di attivazione/disinstallazione (script)</span><span class="sxs-lookup"><span data-stu-id="eec6f-167">Add and configure the Toggle Placement Hints (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="eec6f-168">Il componente Launch Lunar Module (script) e il componente di attivazione/disinstallazione (script) non fanno parte di MRTK.</span><span class="sxs-lookup"><span data-stu-id="eec6f-168">The Launch Lunar Module (Script) component and the Toggle Placement Hints (Script) component are not part of MRTK.</span></span> <span data-ttu-id="eec6f-169">Sono state fornite con le risorse dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="eec6f-169">They were provided with this tutorial's assets.</span></span>

### <a name="1-enable-object-manipulation"></a><span data-ttu-id="eec6f-170">1. abilitare la manipolazione degli oggetti</span><span class="sxs-lookup"><span data-stu-id="eec6f-170">1. Enable object manipulation</span></span>

<span data-ttu-id="eec6f-171">Nella finestra gerarchia selezionare l'oggetto RocketLauncher > **LunarModule** , aggiungere il componente **gestore di manipolazione (script)** e il componente **near Interaction (script)** , quindi configurare il gestore di manipolazione (script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="eec6f-171">In the Hierarchy window, select the RocketLauncher > **LunarModule** object, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="eec6f-172">Modificare il **tipo di manipolazione a due passi** per spostare la rotazione in modo che la scalabilità sia disabilitata</span><span class="sxs-lookup"><span data-stu-id="eec6f-172">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>
* <span data-ttu-id="eec6f-173">Deselezionare la casella di controllo **Consenti modifiche a distanza** per consentire solo l'interazione near</span><span class="sxs-lookup"><span data-stu-id="eec6f-173">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a><span data-ttu-id="eec6f-175">2. abilitare la fisica</span><span class="sxs-lookup"><span data-stu-id="eec6f-175">2. Enable physics</span></span>

<span data-ttu-id="eec6f-176">Con l'oggetto RocketLauncher > **LunarModule** ancora selezionato, aggiungere un componente Rigidbody e quindi configurarlo come segue:</span><span class="sxs-lookup"><span data-stu-id="eec6f-176">With the RocketLauncher > **LunarModule** object still selected, add a Rigidbody component and then configure it as follows:</span></span>

* <span data-ttu-id="eec6f-177">Deselezionare la casella di controllo **USA gravità** per evitare che il modulo Lunar venga influenzato dalla gravità</span><span class="sxs-lookup"><span data-stu-id="eec6f-177">Un-check the **Use Gravity** checkbox so the Lunar Module is not affected by gravity</span></span>
* <span data-ttu-id="eec6f-178">Controllare la casella di controllo **è cinematica** , in modo che il modulo Lunar inizialmente non sia influenzato dalle forze fisiche</span><span class="sxs-lookup"><span data-stu-id="eec6f-178">Check the **Is Kinematic** checkbox so the Lunar Module initially isn't affected by physic forces</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a><span data-ttu-id="eec6f-180">3. aggiungere un componente di origine audio</span><span class="sxs-lookup"><span data-stu-id="eec6f-180">3. Add an Audio Source component</span></span>

<span data-ttu-id="eec6f-181">Con l'oggetto RocketLauncher > **LunarModule** ancora selezionato, aggiungere un componente di **origine audio** e quindi configurarlo come segue:</span><span class="sxs-lookup"><span data-stu-id="eec6f-181">With the RocketLauncher > **LunarModule** object still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="eec6f-182">Modificare **Blend spaziale** su 1 per abilitare l'audio spaziale</span><span class="sxs-lookup"><span data-stu-id="eec6f-182">Change **Spatial Blend** to 1 to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a><span data-ttu-id="eec6f-184">4. aggiungere e configurare il componente Launch Lunar Module (script)</span><span class="sxs-lookup"><span data-stu-id="eec6f-184">4. Add and configure the Launch Lunar Module (Script) component</span></span>

<span data-ttu-id="eec6f-185">Con l'oggetto RocketLauncher > **LunarModule** ancora selezionato, aggiungere il componente **Launch Lunar Module (script)** , quindi configurarlo come segue:</span><span class="sxs-lookup"><span data-stu-id="eec6f-185">With the RocketLauncher > **LunarModule** object still selected, add the **Launch Lunar Module (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="eec6f-186">Modificare il valore di **Spinta** in modo che il modulo lunare si avvicini normalmente all'avvio, ad esempio, a 0,01</span><span class="sxs-lookup"><span data-stu-id="eec6f-186">Change **Thrust** value so the Lunar Module will fly up gracefully when launched, for example, to 0.01</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a><span data-ttu-id="eec6f-188">5. aggiungere e configurare il componente di attivazione/disinstallazione (script)</span><span class="sxs-lookup"><span data-stu-id="eec6f-188">5. Add and configure the Toggle Placement Hints (Script) component</span></span>

<span data-ttu-id="eec6f-189">Con l'oggetto RocketLauncher > **LunarModule** ancora selezionato, aggiungere il componente **interruttore selezione host (script)** e quindi configurarlo come segue:</span><span class="sxs-lookup"><span data-stu-id="eec6f-189">With the RocketLauncher > **LunarModule** object still selected, add the **Toggle Placement Hints (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="eec6f-190">Impostare la proprietà **dimensione** matrice oggetto gioco su 5</span><span class="sxs-lookup"><span data-stu-id="eec6f-190">Set the Game Object Array **Size** property to 5</span></span>
* <span data-ttu-id="eec6f-191">Assegnare ciascuno degli **oggetti figlio** dell'oggetto **PlacementHints** al campo di un **elemento** nella matrice di oggetti del gioco:</span><span class="sxs-lookup"><span data-stu-id="eec6f-191">Assign each of the **PlacementHints** object's **child objects** to the an **Element** field in the Game Object Array:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a><span data-ttu-id="eec6f-193">Configurazione del pulsante Launch</span><span class="sxs-lookup"><span data-stu-id="eec6f-193">Configuring the Launch button</span></span>

<span data-ttu-id="eec6f-194">Nella finestra gerarchia selezionare i pulsanti RocketLauncher > > oggetto **LaunchButton** , quindi, nel componente **pulsante stampabile (script)** , creare un nuovo evento **premuto ()** , configurare l'oggetto **LunarModule** per ricevere l'evento e definire **LaunchLunarModule. StartThruster** come azione da attivare:</span><span class="sxs-lookup"><span data-stu-id="eec6f-194">In the Hierarchy window, select the RocketLauncher > Buttons > **LaunchButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StartThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="eec6f-196">Per un promemoria su come implementare gli eventi, è possibile fare riferimento alle istruzioni per i [movimenti di rilevamento della mano e i pulsanti interagiscono](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) .</span><span class="sxs-lookup"><span data-stu-id="eec6f-196">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

<span data-ttu-id="eec6f-197">Con i pulsanti di > RocketLauncher > oggetto **LaunchButton** ancora selezionato, nel **componente pulsante stampabile (script)** , creare un nuovo **evento premuto ()** , configurare l'oggetto **LunarModule** per ricevere l'evento, definire **audiosource. PlayOneShot** come azione da attivare e assegnare una clip audio adatta al campo **clip** audio, ad esempio il clip audio MRTK_Gem:</span><span class="sxs-lookup"><span data-stu-id="eec6f-197">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

<span data-ttu-id="eec6f-199">Con i pulsanti di > RocketLauncher > oggetto **LaunchButton** ancora selezionato, nel componente **pulsante stampabile (script)** , creare un nuovo evento **touch ended ()** , configurare l'oggetto **LunarModule** per ricevere l'evento e definire **LaunchLunarModule. StopThruster** come azione da attivare:</span><span class="sxs-lookup"><span data-stu-id="eec6f-199">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Touch Ended ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StopThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

<span data-ttu-id="eec6f-201">Se si immette la modalità di gioco e si preme il pulsante Launch (Avvia), si noterà la riproduzione del clip audio. Se si tiene premuto il pulsante Launch (avvio) per circa un secondo o più, verrà visualizzato lo spazio del lancio del modulo Lunar:</span><span class="sxs-lookup"><span data-stu-id="eec6f-201">If you now enter Game mode and press the Launch button, you will hear the audio clip play, and if you hold the Launch button down for about a second or longer, you will see the Lunar Module launch into space:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a><span data-ttu-id="eec6f-203">Configurazione del pulsante Reimposta</span><span class="sxs-lookup"><span data-stu-id="eec6f-203">Configuring the Reset button</span></span>

<span data-ttu-id="eec6f-204">Nella finestra gerarchia selezionare i pulsanti RocketLauncher > > oggetto **ResetButton** , quindi, nel componente **pulsante stampabile (script)** , creare un nuovo evento **premuto ()** , configurare l'oggetto **LunarModule** per ricevere l'evento e definire **LaunchLunarModule. ResetModule** come azione da attivare:</span><span class="sxs-lookup"><span data-stu-id="eec6f-204">In the Hierarchy window, select the RocketLauncher > Buttons > **ResetButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.ResetModule** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

<span data-ttu-id="eec6f-206">Con i pulsanti di > RocketLauncher > oggetto **ResetButton** ancora selezionato, nel **componente pulsante stampabile (script)** , creare un nuovo **evento premuto ()** , configurare l'oggetto **RocketLauncher** per ricevere l'evento, definire **GameObject. BroadcastMessage** come azione da attivare e immettere **ResetPlacement** nel campo messaggio:</span><span class="sxs-lookup"><span data-stu-id="eec6f-206">With the RocketLauncher > Buttons > **ResetButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **RocketLauncher** object to receive the event, define **GameObject.BroadcastMessage** as the action to be triggered, and enter **ResetPlacement** in message field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="eec6f-208">L'azione GameObject. BroadcastMessage invia il messaggio ResetPlacement dall'oggetto RocketLauncher a tutti i relativi oggetti figlio.</span><span class="sxs-lookup"><span data-stu-id="eec6f-208">The GameObject.BroadcastMessage action sends the ResetPlacement message from the RocketLauncher object to all its child object.</span></span> <span data-ttu-id="eec6f-209">Qualsiasi oggetto figlio con la funzione ResetPlacement, definito nel componente Demo assembly parti (script) aggiunto a tutti gli oggetti figlio LunarModuleParts, richiama la funzione ResetPlacement che reimposta la posizione dell'oggetto figlio.</span><span class="sxs-lookup"><span data-stu-id="eec6f-209">Any child object that has the ResetPlacement function, which is defined in the Part Assembly Demo (Script) component you added to all the LunarModuleParts child object, will invoke the ResetPlacement function which resets that child object's placement.</span></span>

<span data-ttu-id="eec6f-210">Se si immette la modalità di gioco e si preme il pulsante Reimposta, il clip audio riprodotto verrà visualizzato e il modulo lunare verrà avviato nello spazio:</span><span class="sxs-lookup"><span data-stu-id="eec6f-210">If you now enter Game mode and press the Reset button you will hear the audio clip being played and see the Lunar Module being launched into space:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="eec6f-212">Configurazione del pulsante degli hint di selezione host</span><span class="sxs-lookup"><span data-stu-id="eec6f-212">Configuring the Placement Hints button</span></span>
<!-- TODO: Rename to 'Configuring the Hints button'-->

<span data-ttu-id="eec6f-213">Nella finestra gerarchia selezionare i pulsanti RocketLauncher > > oggetto **HintsButton** , quindi, nel componente **pulsante stampabile (script)** , creare un nuovo **pulsante premuto ()** , configurare l'oggetto **LunarModule** per ricevere l'evento e definire **TogglePlacementHints. ToggleGameObjects** l'azione da attivare:</span><span class="sxs-lookup"><span data-stu-id="eec6f-213">In the Hierarchy window, select the RocketLauncher > Buttons > **HintsButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **TogglePlacementHints.ToggleGameObjects** the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

<span data-ttu-id="eec6f-215">Se si immette la modalità di gioco, si noterà che gli hint di selezione host traslucidi sono disabilitati per impostazione predefinita, ma è possibile attivarli e disattivarli premendo il pulsante hint:</span><span class="sxs-lookup"><span data-stu-id="eec6f-215">If you now enter Game mode you will notice that the translucent placement hints are disabled by default, but that you can toggle them on and off by pressing the Hints button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="eec6f-217">Complimenti</span><span class="sxs-lookup"><span data-stu-id="eec6f-217">Congratulations</span></span>

<span data-ttu-id="eec6f-218">Questa applicazione è stata configurata completamente.</span><span class="sxs-lookup"><span data-stu-id="eec6f-218">You have fully configured this application.</span></span> <span data-ttu-id="eec6f-219">A questo punto, l'applicazione consente agli utenti di assemblare completamente il modulo Lunar, avviare il modulo Lunar, attivare o disabilitare i suggerimenti e reimpostare l'applicazione in modo che venga riavviata.</span><span class="sxs-lookup"><span data-stu-id="eec6f-219">Now, your application allows users to fully assemble the Lunar Module, launch the Lunar Module, toggle hints, and reset the application to start again.</span></span>

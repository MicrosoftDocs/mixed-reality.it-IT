---
title: Esercitazioni introduttive - 7 Creazione di un'applicazione di esempio Lunar Module
description: In questa lezione combinerai i vari concetti appresi nelle lezioni precedenti per creare un'esperienza di esempio unica.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7b432c5ba0ebee5199f5abb1c26715185fc0d70d
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2020
ms.locfileid: "79031544"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="9848f-105">7. Creazione di un'applicazione di esempio Lunar Module</span><span class="sxs-lookup"><span data-stu-id="9848f-105">7. Creating a Lunar Module sample application</span></span>
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

<span data-ttu-id="9848f-106">In questa esercitazione verranno combinati i vari concetti appresi nelle lezioni precedenti per creare un'esperienza di esempio unica.</span><span class="sxs-lookup"><span data-stu-id="9848f-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="9848f-107">Apprenderai come creare un'applicazione di assembly parti nella quale un utente dovrà usare le mani tracciate per prendere le parti di un modulo lunare e tentare di assemblarlo.</span><span class="sxs-lookup"><span data-stu-id="9848f-107">You will learn how to create a part assembly application whereby a user needs to use tracked hands to pick up parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="9848f-108">Userai pulsanti a pressione per attivare e disattivare i suggerimenti di posizionamento, reimpostare l'esperienza e lanciare il modulo lunare nello spazio.</span><span class="sxs-lookup"><span data-stu-id="9848f-108">You will use pressable buttons to toggle placement hints on and off, to reset the experience, and to launch the lunar module into space!</span></span>

<span data-ttu-id="9848f-109">Nelle esercitazioni successive continuerai a sviluppare questa esperienza, che include efficaci casi d'uso multiutente che sfruttano gli ancoraggi nello spazio di Azure per l'allineamento spaziale.</span><span class="sxs-lookup"><span data-stu-id="9848f-109">In future tutorials, you will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="9848f-110">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="9848f-110">Objectives</span></span>

* <span data-ttu-id="9848f-111">Combinare i vari concetti illustrati nelle lezioni precedenti per creare un'esperienza unica</span><span class="sxs-lookup"><span data-stu-id="9848f-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
* <span data-ttu-id="9848f-112">Apprendere come attivare o disattivare gli oggetti</span><span class="sxs-lookup"><span data-stu-id="9848f-112">Learn how to toggle objects</span></span>
* <span data-ttu-id="9848f-113">Attivare eventi complessi usando i pulsanti a pressione</span><span class="sxs-lookup"><span data-stu-id="9848f-113">Trigger complex events using pressable buttons</span></span>
* <span data-ttu-id="9848f-114">Usare la forza e la fisica dei corpi rigidi</span><span class="sxs-lookup"><span data-stu-id="9848f-114">Use rigidbody physics and forces</span></span>
* <span data-ttu-id="9848f-115">Esplorare l'uso delle descrizioni comandi</span><span class="sxs-lookup"><span data-stu-id="9848f-115">Explore the use of tool tips</span></span>

## <a name="lunar-module-parts-overview"></a><span data-ttu-id="9848f-116">Panoramica delle parti del modulo lunare</span><span class="sxs-lookup"><span data-stu-id="9848f-116">Lunar Module Parts overview</span></span>
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

<span data-ttu-id="9848f-117">In questa sezione creerai una semplice prova di assembly di parti in cui l'obiettivo dell'utente è inserire nella posizione corretta sul modulo lunare cinque parti sparse sul tavolo.</span><span class="sxs-lookup"><span data-stu-id="9848f-117">In this section, you will create a simple part assembly challenge where the user's goal is to place five parts that are spread out on the table at the correct location on the Lunar Module.</span></span>

<span data-ttu-id="9848f-118">Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:</span><span class="sxs-lookup"><span data-stu-id="9848f-118">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="9848f-119">Aggiungere il prefab Rocket Launcher (Lanciamissili) alla scena</span><span class="sxs-lookup"><span data-stu-id="9848f-119">Add the Rocket Launcher prefab to the scene</span></span>
2. <span data-ttu-id="9848f-120">Abilitare la manipolazione degli oggetti per tutte le parti</span><span class="sxs-lookup"><span data-stu-id="9848f-120">Enable object manipulation for all the parts</span></span>
3. <span data-ttu-id="9848f-121">Aggiungere e configurare il componente Part Assembly Demo (Script) (Demo assembly parti - Script)</span><span class="sxs-lookup"><span data-stu-id="9848f-121">Add and configure the Part Assembly Demo (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="9848f-122">Il componente Part Assembly Demo (Script) (Demo assembly parti - Script) non fa parte di MRTK.</span><span class="sxs-lookup"><span data-stu-id="9848f-122">The Part Assembly Demo (Script) component is not part of MRTK.</span></span> <span data-ttu-id="9848f-123">È stato fornito con gli asset dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="9848f-123">It was provided with this tutorial's assets.</span></span>

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a><span data-ttu-id="9848f-124">1. Aggiungere il prefab Rocket Launcher (Lanciamissili) alla scena</span><span class="sxs-lookup"><span data-stu-id="9848f-124">1. Add the Rocket Launcher prefab to the scene</span></span>

<span data-ttu-id="9848f-125">Nella finestra Project (Progetto) passa alla cartella **Assets (Asset)**  > **MRTK.Tutorials.GettingStarted** > **Prefabs (Prefab)**  > **RocketLauncher**, trascina il prefab **RocketLauncher** nella finestra Hierarchy (Gerarchia) per aggiungerlo alla scena e quindi posizionalo in un punto appropriato, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="9848f-125">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher** prefab into the Hierarchy window to add it to your scene, and then position it at a suitable location, for example:</span></span>

* <span data-ttu-id="9848f-126">Trasforma la posizione X = 1.5, Y = -0.4, Z = 0 in modo che venga posizionato a destra dell'utente all'altezza della vita</span><span class="sxs-lookup"><span data-stu-id="9848f-126">Transform Position X = 1.5, Y = -0.4, Z = 0, so it is positioned to the right of the user at waist height</span></span>
* <span data-ttu-id="9848f-127">Trasforma la rotazione X = 0, Y = 180, Z = 0 in modo che le funzionalità principali dell'esperienza siano di fronte all'utente</span><span class="sxs-lookup"><span data-stu-id="9848f-127">Transform Rotation X = 0, Y = 180, Z = 0, so the main features of the experience faces the user</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a><span data-ttu-id="9848f-129">2. Abilitare la manipolazione degli oggetti per tutte le parti</span><span class="sxs-lookup"><span data-stu-id="9848f-129">2. Enable object manipulation for all the parts</span></span>

<span data-ttu-id="9848f-130">Nella finestra Hierarchy (Gerarchia) individua l'oggetto RocketLauncher > **LunarModuleParts** e seleziona tutti gli **oggetti figlio**, aggiungi i componenti **Manipulation Handler (Script)** (Gestore di manipolazione - Script) e **Near Interaction Grabbable (Script)** (Afferrabile con interazione da vicino - Script) e quindi configura il componente Manipulation Handler (Script) (Gestore di manipolazione - Script) come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="9848f-130">In the Hierarchy window, locate the RocketLauncher > **LunarModuleParts** object and select all the **child objects**, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="9848f-131">Deseleziona la casella di controllo **Allow Far Manipulation** (Consenti manipolazione da lontano) per consentire solo l'interazione da vicino</span><span class="sxs-lookup"><span data-stu-id="9848f-131">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="9848f-132">Modifica il campo **Two Handed Manipulation Type** (Tipo di manipolazione a due mani) impostandolo su **Move Rotate** (Spostamento rotazione) in modo da disabilitare il ridimensionamento</span><span class="sxs-lookup"><span data-stu-id="9848f-132">Change **Two Handed Manipulation Type** to **Move Rotate** so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="9848f-134">Per rivedere la procedura di implementazione della manipolazione degli oggetti, con istruzioni dettagliate, puoi fare riferimento alle istruzioni [Manipolare gli oggetti 3D](mrlearning-base-ch4.md#manipulating-3d-objects).</span><span class="sxs-lookup"><span data-stu-id="9848f-134">For a reminder, with step by step instructions, on how to implement object manipulation, you can refer to the [Manipulating 3D Objects](mrlearning-base-ch4.md#manipulating-3d-objects) instructions.</span></span>

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a><span data-ttu-id="9848f-135">3. Aggiungere e configurare il componente Part Assembly Demo (Script) (Demo assembly parti - Script)</span><span class="sxs-lookup"><span data-stu-id="9848f-135">3. Add and configure the Part Assembly Demo (Script) component</span></span>

<span data-ttu-id="9848f-136">Con tutti gli oggetti figlio di LunarModuleParts ancora selezionati, aggiungi un componente **Audio Source** (Origine audio) e quindi configuralo come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="9848f-136">With all the LunarModuleParts child objects still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="9848f-137">Assegna al campo **AudioClip** un clip audio appropriato, ad esempio MRKT_Scale_Start</span><span class="sxs-lookup"><span data-stu-id="9848f-137">Assign a suitable audio clip to the **AudioClip** field, for example, MRKT_Scale_Start</span></span>
* <span data-ttu-id="9848f-138">Deseleziona la casella di controllo **Play On Awake** (Riproduci quando operativo) in modo che il clip audio non venga riprodotto automaticamente durante il caricamento della scena</span><span class="sxs-lookup"><span data-stu-id="9848f-138">Un-check the **Play On Awake** checkbox, so the audio clip does not automatically play when the scene loads</span></span>
* <span data-ttu-id="9848f-139">Modifica il campo **Spatial Blend** (Blend spaziale) impostandolo su 1 per abilitare l'audio spaziale</span><span class="sxs-lookup"><span data-stu-id="9848f-139">Change **Spatial Blend** to 1, to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

<span data-ttu-id="9848f-141">Con tutti gli oggetti figlio di LunarModuleParts ancora selezionati, aggiungi il componente **Part Assembly Demo (Script)** (Demo assembly parti - Script):</span><span class="sxs-lookup"><span data-stu-id="9848f-141">With all the LunarModuleParts child objects still selected, add the **Part Assembly Demo  (Script)** component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

<span data-ttu-id="9848f-143">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **RoverEnclosure** e configura il relativo componente **Part Assembly Demo (Script)** (Demo assembly parti - Script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="9848f-143">In the Hierarchy window, select the **RoverEnclosure** object and configure its **Part Assembly Demo (Script)** component as follows:</span></span>

* <span data-ttu-id="9848f-144">Assegna al campo **Object To Place** (Oggetto da posizionare) l'oggetto **stesso**, in questo caso l'oggetto RoverEnclosure</span><span class="sxs-lookup"><span data-stu-id="9848f-144">To the **Object To Place** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>
* <span data-ttu-id="9848f-145">Assegna al campo **Location To Place** (Punto di posizionamento) l'oggetto **PlacementHints** corrispondente, in questo caso l'oggetto RoverEnclosure_PlacementHint</span><span class="sxs-lookup"><span data-stu-id="9848f-145">To the **Location To Place** field, assign the corresponding **PlacementHints** object, in this case, the RoverEnclosure_PlacementHint object</span></span>
* <span data-ttu-id="9848f-146">Assegna al campo **Tool Tip Object** (Oggetto descrizione comando) l'oggetto **ToolTip** corrispondente, in questo caso l'oggetto RoverEnclosure_ToolTip</span><span class="sxs-lookup"><span data-stu-id="9848f-146">To the **Tool Tip Object** field, assign the corresponding **ToolTip**, in this case, the RoverEnclosure_ToolTip object</span></span>
* <span data-ttu-id="9848f-147">Assegna al campo **Audio Source** (Origine audio) l'oggetto **stesso**, in questo caso l'oggetto RoverEnclosure</span><span class="sxs-lookup"><span data-stu-id="9848f-147">To the **Audio Source** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

<span data-ttu-id="9848f-149">**Ripeti** la procedura per ognuno degli altri oggetti figlio di LunarModuleParts, ad esempio FuelTank, EnergyCell, DockingPortal ed ExternalSensor.</span><span class="sxs-lookup"><span data-stu-id="9848f-149">**Repeat** for each of the other LunarModuleParts child objects, i.e. FuelTank, EnergyCell, DockingPortal, and ExternalSensor.</span></span>

<span data-ttu-id="9848f-150">Se a questo punto attivi la modalità di gioco e sposti un oggetto da posizionare vicino al punto di posizionamento corrispondente, noterai quanto segue:</span><span class="sxs-lookup"><span data-stu-id="9848f-150">If you now enter Game mode and move an 'Object To Place' close to it's corresponding 'Location To Place' you will notice:</span></span>

* <span data-ttu-id="9848f-151">L'oggetto si bloccherà in posizione e gli verrà assegnato un elemento padre nell'oggetto LunarModule in modo che diventi parte del modulo lunare</span><span class="sxs-lookup"><span data-stu-id="9848f-151">The object will snap into place and be parented under the LunarModule object so it becomes part of the Lunar Module</span></span>
* <span data-ttu-id="9848f-152">L'origine audio nell'oggetto riprodurrà il clip audio assegnato nella posizione dell'oggetto</span><span class="sxs-lookup"><span data-stu-id="9848f-152">The Audio Source on the object will play the assigned Audio Clip at the location of the object</span></span>
* <span data-ttu-id="9848f-153">L'oggetto ToolTip corrispondente verrà nascosto</span><span class="sxs-lookup"><span data-stu-id="9848f-153">The corresponding Tool Tip object will be hidden</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> <span data-ttu-id="9848f-155">Per rivedere la procedura di simulazione di input nell'editor, puoi fare riferimento alla guida [Uso della simulazione di input manuale nell'editor per testare una scena](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="9848f-155">For a reminder on how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="configuring-the-lunar-module"></a><span data-ttu-id="9848f-156">Configurazione del modulo lunare</span><span class="sxs-lookup"><span data-stu-id="9848f-156">Configuring the Lunar Module</span></span>

<span data-ttu-id="9848f-157">In questa sezione aggiungerai altre funzionalità all'applicazione Rocket Launcher (Lanciamissili) in modo che l'utente possa:</span><span class="sxs-lookup"><span data-stu-id="9848f-157">In this section, you will add additional features to the Rocket Launcher application so the user can:</span></span>

* <span data-ttu-id="9848f-158">Interagire con il modulo lunare</span><span class="sxs-lookup"><span data-stu-id="9848f-158">Interact with the Lunar Module</span></span>
* <span data-ttu-id="9848f-159">Lanciare il modulo lunare nello spazio e riprodurre un suono quando viene lanciato</span><span class="sxs-lookup"><span data-stu-id="9848f-159">Launch the Lunar Module into space and play a sound when it is launched</span></span>
* <span data-ttu-id="9848f-160">Reimpostare l'applicazione in modo che il modulo lunare e tutte le parti vengano nuovamente riportati nella posizione originale</span><span class="sxs-lookup"><span data-stu-id="9848f-160">Reset the application so the Lunar Module and all the parts are placed back to their original position</span></span>
* <span data-ttu-id="9848f-161">Nascondere i suggerimenti di posizionamento per rendere più difficile la prova di assembly delle parti</span><span class="sxs-lookup"><span data-stu-id="9848f-161">Hide the placement hints to make the part assembly challenge more difficult.</span></span>

<span data-ttu-id="9848f-162">Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:</span><span class="sxs-lookup"><span data-stu-id="9848f-162">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="9848f-163">Abilitare la manipolazione degli oggetti</span><span class="sxs-lookup"><span data-stu-id="9848f-163">Enable object manipulation</span></span>
2. <span data-ttu-id="9848f-164">Abilitare la fisica</span><span class="sxs-lookup"><span data-stu-id="9848f-164">Enable physics</span></span>
3. <span data-ttu-id="9848f-165">Aggiungere un componente Audio Source (Origine audio) all'oggetto</span><span class="sxs-lookup"><span data-stu-id="9848f-165">Add an Audio Source component</span></span>
4. <span data-ttu-id="9848f-166">Aggiungere e configurare il componente Launch Lunar Module (Script) (Lancia modulo lunare - Script)</span><span class="sxs-lookup"><span data-stu-id="9848f-166">Add and configure the Launch Lunar Module (Script) component</span></span>
5. <span data-ttu-id="9848f-167">Aggiungere e configurare il componente Toggle Placement Hints (Script) (Attiva/Disattiva suggerimenti per il posizionamento - Script)</span><span class="sxs-lookup"><span data-stu-id="9848f-167">Add and configure the Toggle Placement Hints (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="9848f-168">I componenti Launch Lunar Module (Script) (Lancia modulo lunare - Script) e Toggle Placement Hints (Script) (Attiva/Disattiva suggerimenti per il posizionamento - Script) non fanno parte di MRTK.</span><span class="sxs-lookup"><span data-stu-id="9848f-168">The Launch Lunar Module (Script) component and the Toggle Placement Hints (Script) component are not part of MRTK.</span></span> <span data-ttu-id="9848f-169">Sono stati forniti con gli asset dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="9848f-169">They were provided with this tutorial's assets.</span></span>

### <a name="1-enable-object-manipulation"></a><span data-ttu-id="9848f-170">1. Abilitare la manipolazione degli oggetti</span><span class="sxs-lookup"><span data-stu-id="9848f-170">1. Enable object manipulation</span></span>

<span data-ttu-id="9848f-171">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto RocketLauncher > **LunarModule**, aggiungi i componenti **Manipulation Handler (Script)** (Gestore di manipolazione - Script) e **Near Interaction Grabbable (Script)** (Afferrabile con interazione da vicino - Script) e configura il componente Manipulation Handler (Script) (Gestore di manipolazione - Script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="9848f-171">In the Hierarchy window, select the RocketLauncher > **LunarModule** object, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="9848f-172">Deseleziona la casella di controllo **Allow Far Manipulation** (Consenti manipolazione da lontano) per consentire solo l'interazione da vicino</span><span class="sxs-lookup"><span data-stu-id="9848f-172">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="9848f-173">Modifica il campo **Two Handed Manipulation Type** (Tipo di manipolazione a due mani) impostandolo su Move Rotate (Spostamento rotazione) in modo da disabilitare il ridimensionamento</span><span class="sxs-lookup"><span data-stu-id="9848f-173">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a><span data-ttu-id="9848f-175">2. Abilitare la fisica</span><span class="sxs-lookup"><span data-stu-id="9848f-175">2. Enable physics</span></span>

<span data-ttu-id="9848f-176">Con l'oggetto RocketLauncher > **LunarModule** ancora selezionato, aggiungi un componente **Rigidbody** e quindi configuralo come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="9848f-176">With the RocketLauncher > **LunarModule** object still selected, add a **Rigidbody** component and then configure it as follows:</span></span>

* <span data-ttu-id="9848f-177">Deseleziona la casella di controllo **Use Gravity** (Usa gravità) in modo che il modulo lunare non sia soggetto a gravità</span><span class="sxs-lookup"><span data-stu-id="9848f-177">Un-check the **Use Gravity** checkbox so the Lunar Module is not affected by gravity</span></span>
* <span data-ttu-id="9848f-178">Seleziona la casella di controllo **Is Kinematic** (Cinematico) in modo che il modulo lunare non sia soggetto inizialmente alle forze della fisica</span><span class="sxs-lookup"><span data-stu-id="9848f-178">Check the **Is Kinematic** checkbox so the Lunar Module initially isn't affected by physic forces</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a><span data-ttu-id="9848f-180">3. Aggiungere un componente Audio Source (Origine audio) all'oggetto</span><span class="sxs-lookup"><span data-stu-id="9848f-180">3. Add an Audio Source component</span></span>

<span data-ttu-id="9848f-181">Con l'oggetto RocketLauncher > **LunarModule** ancora selezionato, aggiungi un componente **Audio Source** (Origine audio) e quindi configuralo come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="9848f-181">With the RocketLauncher > **LunarModule** object still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="9848f-182">Modifica il campo **Spatial Blend** (Blend spaziale) impostandolo su 1 per abilitare l'audio spaziale</span><span class="sxs-lookup"><span data-stu-id="9848f-182">Change **Spatial Blend** to 1 to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a><span data-ttu-id="9848f-184">4. Aggiungere e configurare il componente Launch Lunar Module (Script) (Lancia modulo lunare - Script)</span><span class="sxs-lookup"><span data-stu-id="9848f-184">4. Add and configure the Launch Lunar Module (Script) component</span></span>

<span data-ttu-id="9848f-185">Con l'oggetto RocketLauncher > **LunarModule** ancora selezionato, aggiungi il componente **Launch Lunar Module (Script)** (Lancia modulo lunare - Script) e quindi configuralo come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="9848f-185">With the RocketLauncher > **LunarModule** object still selected, add the **Launch Lunar Module (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="9848f-186">Modifica il valore di **Thrust** (Spinta) in modo che il modulo lunare possa sollevarsi delicatamente quando viene lanciato, impostandolo ad esempio su 0.01</span><span class="sxs-lookup"><span data-stu-id="9848f-186">Change **Thrust** value so the Lunar Module will fly up gracefully when launched, for example, to 0.01</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a><span data-ttu-id="9848f-188">5. Aggiungere e configurare il componente Toggle Placement Hints (Script) (Attiva/Disattiva suggerimenti per il posizionamento - Script)</span><span class="sxs-lookup"><span data-stu-id="9848f-188">5. Add and configure the Toggle Placement Hints (Script) component</span></span>

<span data-ttu-id="9848f-189">Con l'oggetto RocketLauncher > **LunarModule** ancora selezionato, aggiungi il componente **Toggle Placement Hints (Script)** (Attiva/Disattiva suggerimenti per il posizionamento - Script) e quindi configuralo come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="9848f-189">With the RocketLauncher > **LunarModule** object still selected, add the **Toggle Placement Hints (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="9848f-190">Imposta la proprietà **Size** (Dimensione) della matrice degli oggetti gioco su 5</span><span class="sxs-lookup"><span data-stu-id="9848f-190">Set the Game Object Array **Size** property to 5</span></span>
* <span data-ttu-id="9848f-191">Assegna ciascun **oggetto figlio** dell'oggetto RocketLauncher > LunarModule > **PlacementHints** al campo **Element** (Element) nella matrice degli oggetti gioco:</span><span class="sxs-lookup"><span data-stu-id="9848f-191">Assign each of the RocketLauncher > LunarModule > **PlacementHints** object's **child objects** to the an **Element** field in the Game Object Array:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a><span data-ttu-id="9848f-193">Configurazione del pulsante di lancio</span><span class="sxs-lookup"><span data-stu-id="9848f-193">Configuring the Launch button</span></span>

<span data-ttu-id="9848f-194">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto RocketLauncher > Buttons > **LaunchButton**, quindi nel componente **Pressable Button (Script)** (Pulsante a pressione - Script) crea un nuovo evento **Button Pressed ()** (Pulsante premuto), configura l'oggetto **LunarModule** in modo da ricevere l'evento e definisci **LaunchLunarModule.StartThruster** come azione da attivare:</span><span class="sxs-lookup"><span data-stu-id="9848f-194">In the Hierarchy window, select the RocketLauncher > Buttons > **LaunchButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StartThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="9848f-196">Per rivedere la procedura di implementazione degli eventi, puoi fare riferimento alle istruzioni [Movimenti di tracciamento delle mani e pulsanti con supporto per interazioni](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).</span><span class="sxs-lookup"><span data-stu-id="9848f-196">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

<span data-ttu-id="9848f-197">Con l'oggetto RocketLauncher > Buttons > **LaunchButton** ancora selezionato, crea nel componente **Pressable Button (Script)** (Pulsante a pressione - Script) un nuovo evento **Button Pressed ()** (Pulsante premuto), configura l'oggetto **LunarModule** in modo da ricevere l'evento, definisci **AudioSource.PlayOneShot** come azione da attivare e assegna al campo **Audio Clip** (Clip audio) un clip audio appropriato, ad esempio il clip audio MRTK_Gem:</span><span class="sxs-lookup"><span data-stu-id="9848f-197">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

<span data-ttu-id="9848f-199">Con l'oggetto RocketLauncher > Buttons > **LaunchButton** ancora selezionato, crea nel componente **Pressable Button (Script)** (Pulsante a pressione - Script) un nuovo evento **Touch End ()** (Fine tocco), configura l'oggetto **LunarModule** in modo da ricevere l'evento e definisci **LaunchLunarModule.StopThruster** come azione da attivare:</span><span class="sxs-lookup"><span data-stu-id="9848f-199">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Touch End ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StopThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

<span data-ttu-id="9848f-201">Se attivi la modalità di gioco e premi il pulsante di lancio, verrà riprodotto il clip audio. Se tieni premuto il pulsante di lancio per almeno un secondo circa, potrai osservare il lancio del modulo lunare nello spazio:</span><span class="sxs-lookup"><span data-stu-id="9848f-201">If you now enter Game mode and press the Launch button, you will hear the audio clip play, and if you hold the Launch button down for about a second or longer, you will see the Lunar Module launch into space:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a><span data-ttu-id="9848f-203">Configurazione del pulsante di reimpostazione</span><span class="sxs-lookup"><span data-stu-id="9848f-203">Configuring the Reset button</span></span>

<span data-ttu-id="9848f-204">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto RocketLauncher > Buttons > **ResetButton**, quindi nel componente **Pressable Button (Script)** (Pulsante a pressione - Script) crea un nuovo evento **Button Pressed ()** (Pulsante premuto), configura l'oggetto **LunarModule** in modo da ricevere l'evento e definisci **LaunchLunarModule.ResetModule** come azione da attivare:</span><span class="sxs-lookup"><span data-stu-id="9848f-204">In the Hierarchy window, select the RocketLauncher > Buttons > **ResetButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.ResetModule** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

<span data-ttu-id="9848f-206">Con l'oggetto RocketLauncher > Buttons > **ResetButton** ancora selezionato, crea nel componente **Pressable Button (Script)** (Pulsante a pressione - Script) un nuovo evento **Button Pressed ()** (Pulsante premuto), configura l'oggetto **RocketLauncher** in modo da ricevere l'evento, definisci **GameObject.BroadcastMessage** come azione da attivare e immetti **ResetPlacement** nel campo del messaggio:</span><span class="sxs-lookup"><span data-stu-id="9848f-206">With the RocketLauncher > Buttons > **ResetButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **RocketLauncher** object to receive the event, define **GameObject.BroadcastMessage** as the action to be triggered, and enter **ResetPlacement** in message field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="9848f-208">L'azione GameObject.BroadcastMessage invia il messaggio ResetPlacement dall'oggetto RocketLauncher a tutti i relativi oggetti figlio.</span><span class="sxs-lookup"><span data-stu-id="9848f-208">The GameObject.BroadcastMessage action sends the ResetPlacement message from the RocketLauncher object to all its child object.</span></span> <span data-ttu-id="9848f-209">Gli oggetti figlio con la funzione ResetPlacement, definita nel componente Part Assembly Demo (Script) (Demo assembly parti - Script) aggiunto a tutti gli oggetti figlio LunarModuleParts, richiameranno la funzione ResetPlacement che reimposta la posizione dell'oggetto figlio.</span><span class="sxs-lookup"><span data-stu-id="9848f-209">Any child object that has the ResetPlacement function, which is defined in the Part Assembly Demo (Script) component you added to all the LunarModuleParts child object, will invoke the ResetPlacement function which resets that child object's placement.</span></span>

<span data-ttu-id="9848f-210">Se attivi ora la modalità di gioco, sposti alcune parti e/o avvii il modulo lunare e quindi premi il pulsante Reimposta, visualizzerai le parti e/o il modulo lunare da reimpostare nella posizione originale:</span><span class="sxs-lookup"><span data-stu-id="9848f-210">If you now enter Game mode, move some parts and/or launch the Lunar Module, and then press the Reset button you will see the parts and/or the Lunar Module being reset to their original position:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="9848f-212">Configurazione del pulsante dei suggerimenti di posizionamento</span><span class="sxs-lookup"><span data-stu-id="9848f-212">Configuring the Placement Hints button</span></span>
<!-- TODO: Rename to 'Configuring the Hints button'-->

<span data-ttu-id="9848f-213">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto RocketLauncher > Buttons > **HintsButton**, quindi nel componente **Pressable Button (Script)** (Pulsante a pressione - Script) crea un nuovo evento **Button Pressed ()** (Pulsante premuto), configura l'oggetto **LunarModule** in modo da ricevere l'evento e definisci **TogglePlacementHints.ToggleGameObjects** come azione da attivare:</span><span class="sxs-lookup"><span data-stu-id="9848f-213">In the Hierarchy window, select the RocketLauncher > Buttons > **HintsButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **TogglePlacementHints.ToggleGameObjects** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

<span data-ttu-id="9848f-215">Se attivi ora la modalità di gioco, noterai che i suggerimenti di posizionamento traslucidi sono disabilitati per impostazione predefinita, ma puoi attivarli e disattivarli premendo il pulsante Hints (Suggerimenti):</span><span class="sxs-lookup"><span data-stu-id="9848f-215">If you now enter Game mode you will notice that the translucent placement hints are disabled by default, but that you can toggle them on and off by pressing the Hints button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="9848f-217">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="9848f-217">Congratulations</span></span>

<span data-ttu-id="9848f-218">Hai configurato completamente questa applicazione.</span><span class="sxs-lookup"><span data-stu-id="9848f-218">You have fully configured this application.</span></span> <span data-ttu-id="9848f-219">A questo punto, l'applicazione consente agli utenti di assemblare completamente il modulo lunare, lanciarlo, attivare o disattivare i suggerimenti e reimpostare l'applicazione in modo che venga riavviata.</span><span class="sxs-lookup"><span data-stu-id="9848f-219">Now, your application allows users to fully assemble the Lunar Module, launch the Lunar Module, toggle hints, and reset the application to start again.</span></span>

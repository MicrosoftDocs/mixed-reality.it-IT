---
title: Esercitazioni introduttive - 4 Inserimento di contenuto dinamico e uso dei risolutori
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 8a85ab560d0e6b36b589970b4d5b8a441ed2bbe2
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362037"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="1266d-105">4. Inserimento di contenuto dinamico e uso dei risolutori</span><span class="sxs-lookup"><span data-stu-id="1266d-105">4. Placing dynamic content and using Solvers</span></span>
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

<span data-ttu-id="1266d-106">Gli ologrammi prendono vita in HoloLens 2 quando seguono l'utente in modo intuitivo e vengono posizionati nell'ambiente fisico in modo da rendere l'interazione semplice ed elegante.</span><span class="sxs-lookup"><span data-stu-id="1266d-106">Holograms come to life in HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="1266d-107">In questa esercitazione verranno analizzate le modalità per posizionare in modo dinamico gli ologrammi usando gli strumenti di posizionamento disponibili in MRTK, noti come "risolutori", per risolvere scenari complessi di posizionamento nello spazio.</span><span class="sxs-lookup"><span data-stu-id="1266d-107">In this tutorial, we explore ways to dynamically place holograms using the MRTK's available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="1266d-108">In MRTK i risolutori costituiscono un sistema di script e comportamenti usati per consentire agli elementi dell'interfaccia utente di seguire te, l'utente o altri oggetti gioco nella scena.</span><span class="sxs-lookup"><span data-stu-id="1266d-108">In the MRTK, Solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="1266d-109">Possono anche essere usati per l'ancoraggio rapido a determinate posizioni, rendendo così più intuitiva l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="1266d-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="1266d-110">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="1266d-110">Objectives</span></span>

* <span data-ttu-id="1266d-111">Illustrare i risolutori di MRTK</span><span class="sxs-lookup"><span data-stu-id="1266d-111">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="1266d-112">Usare i risolutori per fare in modo che una raccolta di pulsanti segua l'utente</span><span class="sxs-lookup"><span data-stu-id="1266d-112">Use Solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="1266d-113">Usare i risolutori per fare in modo che un oggetto gioco segua le mani tracciate dell'utente</span><span class="sxs-lookup"><span data-stu-id="1266d-113">Use Solvers to have a game object follow the user's tracked hands</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="1266d-114">Posizione dei risolutori in MRTK</span><span class="sxs-lookup"><span data-stu-id="1266d-114">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="1266d-115">I risolutori di MRTK si trovano nella cartella MRTK SDK.</span><span class="sxs-lookup"><span data-stu-id="1266d-115">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="1266d-116">Per visualizzare i risolutori disponibili in un progetto, nella finestra Project (Progetto) passa a **Assets (Asset)**  > **MixedRealityToolkit.SDK** > **Features (Funzionalità)**  > **Utilities (Utilità)**  > **Solvers** (Risolutori):</span><span class="sxs-lookup"><span data-stu-id="1266d-116">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

<span data-ttu-id="1266d-118">In questa esercitazione verrà esaminata l'implementazione dei risolutori Orbital (Orbitale) e Radial View (Vista radiale).</span><span class="sxs-lookup"><span data-stu-id="1266d-118">In this tutorial, we will review the implementation of the Orbital Solver and the Radial View Solver.</span></span> <span data-ttu-id="1266d-119">Per altre informazioni sull'intera gamma di risolutori disponibili in MRTK, puoi fare riferimento alla guida [Risolutori](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) nel [portale della documentazione si MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="1266d-119">To learn more about the full range of Solvers available in the MRTK, you can visit the the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="1266d-120">Usare un risolutore per seguire l'utente</span><span class="sxs-lookup"><span data-stu-id="1266d-120">Use a Solver to follow the user</span></span>
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

<span data-ttu-id="1266d-121">In questa sezione verrà migliorata la raccolta di pulsanti creata nell'esercitazione precedente in modo che segua la direzione dello sguardo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="1266d-121">In this section, you will enhance the button collection you created in the previous tutorial so it follows the user's gaze direction.</span></span> <span data-ttu-id="1266d-122">Inoltre, il risolutore verrà configurato in modo che la raccolta di pulsanti sia sempre:</span><span class="sxs-lookup"><span data-stu-id="1266d-122">Additionally, you will also configure the Solver so the button collection is always:</span></span>

* <span data-ttu-id="1266d-123">Ruotata in parallelo rispetto alla direzione di lettura dell'utente, per la lettura naturale da sinistra a destra</span><span class="sxs-lookup"><span data-stu-id="1266d-123">Rotated parallel to the user's reading direction, for natural left to right reading</span></span>
* <span data-ttu-id="1266d-124">Posizionata al di sotto della direzione dello sguardo orizzontale dell'utente in modo da non ostacolare gli altri oggetti che aggiungerai più avanti in questa esercitazione</span><span class="sxs-lookup"><span data-stu-id="1266d-124">Positioned below the user horizontal gaze direction, so it's not obstructing the other objects you will add later in this tutorial</span></span>
* <span data-ttu-id="1266d-125">Posizionata approssimativamente a metà della portata di braccio dell'utente, in modo che sia possibile selezionare facilmente i pulsanti</span><span class="sxs-lookup"><span data-stu-id="1266d-125">Positioned approximately a half arm's-length from the user, so the buttons can easily be pressed</span></span>

<span data-ttu-id="1266d-126">A tale scopo, userai il **risolutore Orbital (Orbitale)** che blocca l'oggetto in una posizione e con un offset specifici rispetto all'oggetto di riferimento.</span><span class="sxs-lookup"><span data-stu-id="1266d-126">For this, you will use the **Orbital Solver** which locks the object to a specified position and offset from the referenced object.</span></span>

### <a name="1-add-the-orbital-solver"></a><span data-ttu-id="1266d-127">1. Aggiungere il risolutore Orbital (Orbitale)</span><span class="sxs-lookup"><span data-stu-id="1266d-127">1. Add the Orbital Solver</span></span>

<span data-ttu-id="1266d-128">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **ButtonCollection**, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Orbital (Script)** (Orbitale - Script) all'oggetto ButtonCollection.</span><span class="sxs-lookup"><span data-stu-id="1266d-128">In the Hierarchy window, select the **ButtonCollection** object, then in the Inspector window, use the **Add Component** button to add the **Orbital (Script)** component to the ButtonCollection object.</span></span>

> [!NOTE]
> <span data-ttu-id="1266d-129">Quando aggiungi un risolutore, in questo caso il componente Orbital (Script) (Orbitale - Script), viene aggiunto automaticamente il componente Solver Handler (Script) (Gestore risolutori - Script) perché è richiesto dal risolutore.</span><span class="sxs-lookup"><span data-stu-id="1266d-129">When you add a Solver, in this case the Orbital (Script) component, the Solver Handler (Script) component is automatically added because it is required by the Solver.</span></span>

### <a name="2-configure-the-orbital-solver"></a><span data-ttu-id="1266d-130">2. Configurare il risolutore Orbital (Orbitale)</span><span class="sxs-lookup"><span data-stu-id="1266d-130">2. Configure the Orbital Solver</span></span>

<span data-ttu-id="1266d-131">Configura il componente **Solver Handler (Script)** (Gestore risolutori - Script):</span><span class="sxs-lookup"><span data-stu-id="1266d-131">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="1266d-132">Verifica che per **Tracked Target Type** (Tipo destinazione tracciata) sia impostato il valore **Head** (Testa)</span><span class="sxs-lookup"><span data-stu-id="1266d-132">Verify that **Tracked Target Type** is set to **Head**</span></span>

<span data-ttu-id="1266d-133">Configura il componente **Orbital (Script)** (Orbitale - Script):</span><span class="sxs-lookup"><span data-stu-id="1266d-133">Configure the **Orbital (Script)** component:</span></span>

* <span data-ttu-id="1266d-134">Verifica che per **Orientation Type** (Tipo di orientamento) sia impostato il valore **Follow Tracked Object** (Segui oggetto tracciato)</span><span class="sxs-lookup"><span data-stu-id="1266d-134">Verify that **Orientation Type** is set to **Follow Tracked Object**</span></span>
* <span data-ttu-id="1266d-135">Reimposta **Local Offset** (Offset locale) su X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="1266d-135">Reset **Local Offset** to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="1266d-136">Modifica il valore di **World Offset** (Offset globale) impostando X = 0, Y = -0.4, Z = 0.3</span><span class="sxs-lookup"><span data-stu-id="1266d-136">Change **World Offset** to X = 0, Y = -0.4, Z = 0.3</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a><span data-ttu-id="1266d-138">3. Testare il risolutore Orbital (Orbitale) usando la simulazione nell'editor</span><span class="sxs-lookup"><span data-stu-id="1266d-138">3. Test the Orbital Solver using the in-editor simulation</span></span>

<span data-ttu-id="1266d-139">Seleziona il pulsante Play (Riproduci) per attivare la modalità di gioco e tieni premuto il pulsante destro del mouse per ruotare la direzione dello sguardo. Potrai osservare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="1266d-139">Press the Play button to enter Game mode and press and hold the right mouse button to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="1266d-140">La posizione di trasformazione di ButtonCollection è ora determinata dalle impostazioni del risolutore</span><span class="sxs-lookup"><span data-stu-id="1266d-140">The ButtonCollection's Transform Position is now driven by the Solver settings</span></span>
* <span data-ttu-id="1266d-141">L'oggetto Cube, che non è influenzato dal risolutore, rimane nella stessa posizione</span><span class="sxs-lookup"><span data-stu-id="1266d-141">The Cube, which is not affected by the Solver, remains in the same position</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> <span data-ttu-id="1266d-143">Se il raggio della fotocamera non è visibile nella finestra della scena, verifica che sia attivato il menu Gizmos.</span><span class="sxs-lookup"><span data-stu-id="1266d-143">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled.</span></span> <span data-ttu-id="1266d-144">Per altre informazioni sul menu Gizmos e su come è possibile usarlo per ottimizzare la vista della scena, puoi fare riferimento alla documentazione relativa al <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">menu Gizmos</a> di Unity.</span><span class="sxs-lookup"><span data-stu-id="1266d-144">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can visit Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>
>
> <span data-ttu-id="1266d-145">Per visualizzare le finestre della scena e di gioco affiancate, come mostrato nell'immagine precedente, trascina semplicemente la finestra di gioco a destra della finestra della scena.</span><span class="sxs-lookup"><span data-stu-id="1266d-145">To display your Scene and Game window side by side as shown in the image above, simply drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="1266d-146">Per altre informazioni sulla personalizzazione dell'area di lavoro, puoi fare riferimento alla documentazione <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> (Personalizzazione dell'area di lavoro) di Unity.</span><span class="sxs-lookup"><span data-stu-id="1266d-146">To learn more about customizing your workspace, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

## <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="1266d-147">Consentire agli oggetti di seguire le mani tracciate</span><span class="sxs-lookup"><span data-stu-id="1266d-147">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="1266d-148">In questa sezione verrà configurato l'oggetto Cube creato nell'esercitazione precedente in modo che segua le mani tracciate dell'utente, in particolare il polso destro.</span><span class="sxs-lookup"><span data-stu-id="1266d-148">In this section, you will configure the Cube object you created in the previous tutorial so it follows the user's tracked hands, specifically the right hand wrist.</span></span> <span data-ttu-id="1266d-149">Inoltre, il risolutore verrà configurato in modo che il cubo:</span><span class="sxs-lookup"><span data-stu-id="1266d-149">Additionally, you will also configure the Solver so the cube:</span></span>

* <span data-ttu-id="1266d-150">Modifichi il proprio orientamento con la rotazione della mano dell'utente</span><span class="sxs-lookup"><span data-stu-id="1266d-150">Changes it's orientation with the user's hand rotation</span></span>
* <span data-ttu-id="1266d-151">Sia posizionato sul polso dell'utente</span><span class="sxs-lookup"><span data-stu-id="1266d-151">Positioned on the user's wrist</span></span>

<span data-ttu-id="1266d-152">A tale scopo, userai il **risolutore Radial View** (Vista radiale) che mantiene l'oggetto all'interno di un cono di visione formato dall'oggetto di riferimento.</span><span class="sxs-lookup"><span data-stu-id="1266d-152">For this, you will use the **Radial View Solver** which keeps the object within a view cone cast by the referenced object.</span></span>

### <a name="1-add-the-radial-view-solver"></a><span data-ttu-id="1266d-153">1. Aggiungere il risolutore Radial View (Vista radiale)</span><span class="sxs-lookup"><span data-stu-id="1266d-153">1. Add the Radial View Solver</span></span>

<span data-ttu-id="1266d-154">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Cube**, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Radial View (Script)** (Vista radiale - Script) all'oggetto Cube.</span><span class="sxs-lookup"><span data-stu-id="1266d-154">In the Hierarchy window, select the **Cube** object, then in the Inspector window, use the **Add Component** button to add the **Radial View (Script)** component Cube object.</span></span>

### <a name="2-configure-the-radial-view-solver"></a><span data-ttu-id="1266d-155">2. Configurare il risolutore Radial View (Vista radiale)</span><span class="sxs-lookup"><span data-stu-id="1266d-155">2. Configure the Radial View Solver</span></span>

<span data-ttu-id="1266d-156">Configura il componente **Solver Handler (Script)** (Gestore risolutori - Script):</span><span class="sxs-lookup"><span data-stu-id="1266d-156">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="1266d-157">Modifica il campo **Tracked Target Type** (Tipo destinazione tracciata) impostandolo su **Hand Joint** (Articolazione mano)</span><span class="sxs-lookup"><span data-stu-id="1266d-157">Change **Tracked Target Type** to **Hand Joint**</span></span>
* <span data-ttu-id="1266d-158">Modifica il campo **Tracked Handness** (Manualità tracciata) impostandolo su **Right** (Destra)</span><span class="sxs-lookup"><span data-stu-id="1266d-158">Change **Tracked Handness** to **Right**</span></span>
* <span data-ttu-id="1266d-159">Modifica il campo **Tracked Hand Joint** (Articolazione mano tracciata) impostandolo su **Wrist** (Polso)</span><span class="sxs-lookup"><span data-stu-id="1266d-159">Change **Tracked Hand Joint** to **Wrist**</span></span>

<span data-ttu-id="1266d-160">Configura il componente **Radial View (Script)** (Vista radiale - Script):</span><span class="sxs-lookup"><span data-stu-id="1266d-160">Configure the **Radial View (Script)** component:</span></span>

* <span data-ttu-id="1266d-161">Modifica il campo **Reference Direction** (Direzione di riferimento) impostandolo su **Object Oriented** (Orientamento verso l'oggetto), quindi seleziona la casella di controllo **Orient To Reference Direction** (Orienta verso direzione di riferimento)</span><span class="sxs-lookup"><span data-stu-id="1266d-161">Change **Reference Direction** to **Object Oriented**, then check the **Orient To Reference Direction** checkbox</span></span>
* <span data-ttu-id="1266d-162">Modifica i campi **Min Distance** (Distanza min) e **Max Distance** (Distanza max) impostandoli su 0</span><span class="sxs-lookup"><span data-stu-id="1266d-162">Change **Min Distance** and **Max Distance** to 0</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a><span data-ttu-id="1266d-164">3. Testare il risolutore Radial View (Vista radiale) usando la simulazione nell'editor</span><span class="sxs-lookup"><span data-stu-id="1266d-164">3. Test the Radial View Solver using the in-editor simulation</span></span>

<span data-ttu-id="1266d-165">Seleziona il pulsante Play (Riproduci) per attivare la modalità di gioco e quindi tieni premuta la barra spaziatrice per portare in alto la mano.</span><span class="sxs-lookup"><span data-stu-id="1266d-165">Press the Play button to enter Game mode and then press and hold the spacebar to bring up the hand.</span></span> <span data-ttu-id="1266d-166">Sposta il cursore del mouse per muovere la mano, quindi fai clic e tieni premuto il pulsante sinistro del mouse per ruotare la mano:</span><span class="sxs-lookup"><span data-stu-id="1266d-166">Move the mouse cursor around to move the hand, and click and hold the left mouse button to rotate the hand:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a><span data-ttu-id="1266d-168">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="1266d-168">Congratulations</span></span>

<span data-ttu-id="1266d-169">In questa esercitazione hai appreso come usare i risolutori di MRTK affinché l'interfaccia utente segua l'utente in modo intuitivo.</span><span class="sxs-lookup"><span data-stu-id="1266d-169">In this tutorial, you learned how to use the MRTK's solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="1266d-170">Hai anche appreso come collegare un risolutore a un oggetto (ad esempio un cubo) per seguire le mani tracciate dell'utente.</span><span class="sxs-lookup"><span data-stu-id="1266d-170">You also learned how to attach a Solver to an object (i.e., cube) to follow the user's tracked hands.</span></span> <span data-ttu-id="1266d-171">Per altre informazioni su questi e altri risolutori inclusi in MRTK, puoi fare riferimento alla pagina [Risolutori](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) nel [portale dei risolutori di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="1266d-171">To learn more about these and other solvers included with the MRTK,  you can visit the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="1266d-172">Esercitazione successiva: 5. Interazione con oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="1266d-172">Next Tutorial: 5. Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)

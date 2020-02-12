---
title: Esercitazione introduttiva-4. Inserimento di contenuto dinamico e utilizzo di risolutori
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 8275d5a97d7827d34ed3926cabe4032cc7f4cfac
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129327"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="76508-105">4. posizionamento del contenuto dinamico e utilizzo dei risolutori</span><span class="sxs-lookup"><span data-stu-id="76508-105">4. Placing dynamic content and using Solvers</span></span>
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

<span data-ttu-id="76508-106">Gli ologrammi entrano a far parte di HoloLens 2 quando seguono in modo intuitivo l'utente e vengono inseriti nell'ambiente fisico in modo da rendere l'interazione semplice ed elegante.</span><span class="sxs-lookup"><span data-stu-id="76508-106">Holograms come to life in HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="76508-107">In questa esercitazione vengono illustrate le modalità per posizionare in modo dinamico gli ologrammi usando gli strumenti di posizionamento disponibili di MRTK, noti come risolutori, per risolvere scenari di posizionamento spaziali complessi.</span><span class="sxs-lookup"><span data-stu-id="76508-107">In this tutorial, we explore ways to dynamically place holograms using the MRTK’s available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="76508-108">In MRTK, i risolutori sono un sistema di script e comportamenti usati per consentire agli elementi dell'interfaccia utente di seguire l'utente, l'utente o altri oggetti del gioco nella scena.</span><span class="sxs-lookup"><span data-stu-id="76508-108">In the MRTK, Solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="76508-109">Possono anche essere usati per l'ancoraggio rapido a determinate posizioni, rendendo così più intuitiva l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="76508-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="76508-110">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="76508-110">Objectives</span></span>

* <span data-ttu-id="76508-111">Introdurre i risolutori di MRTK</span><span class="sxs-lookup"><span data-stu-id="76508-111">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="76508-112">Usare i resolver per avere una raccolta di pulsanti che seguono l'utente</span><span class="sxs-lookup"><span data-stu-id="76508-112">Use Solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="76508-113">Usare i resolver per fare in modo che un oggetto gioco segua le lancette rilevate dall'utente</span><span class="sxs-lookup"><span data-stu-id="76508-113">Use Solvers to have a game object follow the user's tracked hands</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="76508-114">Percorso dei risolutori in MRTK</span><span class="sxs-lookup"><span data-stu-id="76508-114">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="76508-115">I risolutori di MRTK si trovano nella cartella SDK di MRTK.</span><span class="sxs-lookup"><span data-stu-id="76508-115">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="76508-116">Per visualizzare i resolver disponibili nel progetto, nella finestra del progetto passare a **assets** > **MixedRealityToolkit. SDK** > **features** > **Utilities** > **Resolvers**:</span><span class="sxs-lookup"><span data-stu-id="76508-116">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

<span data-ttu-id="76508-118">In questa esercitazione verrà esaminata l'implementazione del Risolutore orbitale e del Risolutore di viste radiali.</span><span class="sxs-lookup"><span data-stu-id="76508-118">In this tutorial, we will review the implementation of the Orbital Solver and the Radial View Solver.</span></span> <span data-ttu-id="76508-119">Per altre informazioni sull'intera gamma di resolver disponibili in MRTK, vedere la guida per i [risolutori](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) nel portale della documentazione di [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="76508-119">To learn more about the full range of Solvers available in the MRTK, you can visit the the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="76508-120">Usare un Risolutore per seguire l'utente</span><span class="sxs-lookup"><span data-stu-id="76508-120">Use a Solver to follow the user</span></span>
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

<span data-ttu-id="76508-121">In questa sezione verrà migliorata la raccolta dei pulsanti creata nell'esercitazione precedente in modo che segua la direzione dello sguardo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="76508-121">In this section, you will enhance the button collection you created in the previous tutorial so it follows the user’s gaze direction.</span></span> <span data-ttu-id="76508-122">Inoltre, verrà configurato anche il Risolutore, in modo che la raccolta dei pulsanti sia sempre:</span><span class="sxs-lookup"><span data-stu-id="76508-122">Additionally, you will also configure the Solver so the button collection is always:</span></span>

* <span data-ttu-id="76508-123">Ruotato in parallelo alla direzione di lettura dell'utente, per la lettura naturale da sinistra a destra</span><span class="sxs-lookup"><span data-stu-id="76508-123">Rotated parallel to the user's reading direction, for natural left to right reading</span></span>
* <span data-ttu-id="76508-124">Posizionato leggermente sotto la direzione degli sguardi orizzontali dell'utente, quindi non ostruisce gli altri oggetti che verrà aggiunto più avanti in questa esercitazione</span><span class="sxs-lookup"><span data-stu-id="76508-124">Positioned slightly below the user horizontal gaze direction, so it's not obstructing the other objects you will add later in this tutorial</span></span>
* <span data-ttu-id="76508-125">Posizionato approssimativamente a metà del braccio dall'utente, quindi è possibile premere facilmente i pulsanti</span><span class="sxs-lookup"><span data-stu-id="76508-125">Positioned approximately a half arm's-length from the user, so the buttons can easily be pressed</span></span>

<span data-ttu-id="76508-126">A tale scopo, si utilizzerà il **Risolutore orbitale** che blocca l'oggetto in una posizione e un offset specificati dall'oggetto a cui si fa riferimento.</span><span class="sxs-lookup"><span data-stu-id="76508-126">For this, you will use the **Orbital Solver** which locks the object to a specified position and offset from the referenced object.</span></span>

### <a name="1-add-the-orbital-solver"></a><span data-ttu-id="76508-127">1. aggiungere il Risolutore orbitale</span><span class="sxs-lookup"><span data-stu-id="76508-127">1. Add the Orbital Solver</span></span>

<span data-ttu-id="76508-128">Nella finestra gerarchia selezionare l'oggetto **buttoncollection** , quindi nella finestra di controllo usare il pulsante **Aggiungi componente** per aggiungere il componente **Orbital (script)** all'oggetto buttoncollection.</span><span class="sxs-lookup"><span data-stu-id="76508-128">In the Hierarchy window, select the **ButtonCollection** object, then in the Inspector window, use the **Add Component** button to add the **Orbital (Script)** component to the ButtonCollection object.</span></span>

> [!NOTE]
> <span data-ttu-id="76508-129">Quando si aggiunge un Risolutore, in questo caso il componente Orbital (script), il componente di gestione del Risolutore (script) viene aggiunto automaticamente perché è necessario per il Risolutore.</span><span class="sxs-lookup"><span data-stu-id="76508-129">When you add a Solver, in this case the Orbital (Script) component, the Solver Handler (Script) component is automatically added because it is required by the Solver.</span></span>

### <a name="2-configure-the-orbital-solver"></a><span data-ttu-id="76508-130">2. configurare il Risolutore di orbitali</span><span class="sxs-lookup"><span data-stu-id="76508-130">2. Configure the Orbital Solver</span></span>

<span data-ttu-id="76508-131">Configurare il componente **gestore Risolutore (script)** :</span><span class="sxs-lookup"><span data-stu-id="76508-131">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="76508-132">Verificare che il **tipo di destinazione rilevata** sia impostato su **Head**</span><span class="sxs-lookup"><span data-stu-id="76508-132">Verify that **Tracked Target Type**  is set to **Head**</span></span>

<span data-ttu-id="76508-133">Configurare il componente **Orbital (script)** :</span><span class="sxs-lookup"><span data-stu-id="76508-133">Configure the **Orbital (Script)** component:</span></span>

* <span data-ttu-id="76508-134">Modificare il **tipo di orientamento** per seguire l' **oggetto rilevato**</span><span class="sxs-lookup"><span data-stu-id="76508-134">Change **Orientation Type** to **Follow Tracked Object**</span></span>
* <span data-ttu-id="76508-135">Reimposta **offset locale** su X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="76508-135">Reset **Local Offset** to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="76508-136">Imposta **offset globale** su X = 0, Y =-0,4, Z = 0,3</span><span class="sxs-lookup"><span data-stu-id="76508-136">Change **World Offset** to X = 0, Y = -0.4, Z = 0.3</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a><span data-ttu-id="76508-138">3. testare il Risolutore Orbital usando la simulazione in-Editor</span><span class="sxs-lookup"><span data-stu-id="76508-138">3. Test the Orbital Solver using the in-editor simulation</span></span>

<span data-ttu-id="76508-139">Premere il pulsante Riproduci per attivare la modalità di gioco e premere e tenere premuto il pulsante destro del mouse per ruotare la direzione dello sguardo e notare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="76508-139">Press the Play button to enter Game mode and press and hold the right mouse button to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="76508-140">La posizione di trasformazione di Buttoncollection è ora determinata dalle impostazioni del Risolutore</span><span class="sxs-lookup"><span data-stu-id="76508-140">The ButtonCollection's Transform Position is now driven by the Solver settings</span></span>
* <span data-ttu-id="76508-141">Il cubo, che non è influenzato dal Risolutore, rimane nella stessa posizione</span><span class="sxs-lookup"><span data-stu-id="76508-141">The Cube, which is not affected by the Solver, remains in the same position</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> <span data-ttu-id="76508-143">Se il raggio della fotocamera non è visibile nella finestra della scena, verificare che il menu gizmos sia abilitato.</span><span class="sxs-lookup"><span data-stu-id="76508-143">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled.</span></span> <span data-ttu-id="76508-144">Per altre informazioni sul menu gizmos e su come usarlo per ottimizzare la visualizzazione della scena, è possibile visitare la documentazione del <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">menu dei gizmo</a> di Unity.</span><span class="sxs-lookup"><span data-stu-id="76508-144">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can visit Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>
>
> <span data-ttu-id="76508-145">Per visualizzare la scena e la finestra di gioco affiancata, come illustrato nell'immagine precedente, trascinare semplicemente la finestra del gioco sul lato destro della finestra della scena.</span><span class="sxs-lookup"><span data-stu-id="76508-145">To display your Scene and Game window side by side as shown in the image above, simply drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="76508-146">Per ulteriori informazioni sulla personalizzazione dell'area di lavoro, è possibile visitare la pagina relativa alla <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">personalizzazione dell'area di lavoro</a> di Unity.</span><span class="sxs-lookup"><span data-stu-id="76508-146">To learn more about customizing your workspace, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

## <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="76508-147">Abilitazione degli oggetti per seguire le mani tracciate</span><span class="sxs-lookup"><span data-stu-id="76508-147">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="76508-148">In questa sezione si configurerà l'oggetto cubo creato nell'esercitazione precedente, in modo che segua le mani rilevate dall'utente, in particolare il polso destro.</span><span class="sxs-lookup"><span data-stu-id="76508-148">In this section, you will configure the Cube object you created in the previous tutorial so it follows the user’s tracked hands, specifically the right hand wrist.</span></span> <span data-ttu-id="76508-149">Inoltre, il Risolutore viene configurato in modo che il cubo:</span><span class="sxs-lookup"><span data-stu-id="76508-149">Additionally, you will also configure the Solver so the cube:</span></span>

* <span data-ttu-id="76508-150">Modifica l'orientamento con la rotazione a mano dell'utente</span><span class="sxs-lookup"><span data-stu-id="76508-150">Changes it's orientation with the user's hand rotation</span></span>
* <span data-ttu-id="76508-151">Posizionato sul polso dell'utente</span><span class="sxs-lookup"><span data-stu-id="76508-151">Positioned on the user's wrist</span></span>

<span data-ttu-id="76508-152">A tale scopo, si utilizzerà il **Risolutore di viste radiali** , che consente di mantenere l'oggetto all'interno di un cono di visualizzazione di cui viene eseguito il cast dall'oggetto</span><span class="sxs-lookup"><span data-stu-id="76508-152">For this, you will use the **Radial View Solver** which keeps the object within a view cone cast by the referenced object.</span></span>

### <a name="1-add-the-radial-view-solver"></a><span data-ttu-id="76508-153">1. aggiungere il Risolutore di visualizzazione radiale</span><span class="sxs-lookup"><span data-stu-id="76508-153">1. Add the Radial View Solver</span></span>

<span data-ttu-id="76508-154">Nella finestra gerarchia selezionare l'oggetto **cubo** , quindi nella finestra di controllo usare il pulsante **Aggiungi componente** per aggiungere l'oggetto del cubo del componente di **visualizzazione radiale (script)** .</span><span class="sxs-lookup"><span data-stu-id="76508-154">In the Hierarchy window, select the **Cube** object, then in the Inspector window, use the **Add Component** button to add the **Radial View (Script)** component Cube object.</span></span>

### <a name="2-configure-the-radial-view-solver"></a><span data-ttu-id="76508-155">2. configurare il Risolutore di viste radiali</span><span class="sxs-lookup"><span data-stu-id="76508-155">2. Configure the Radial View Solver</span></span>

<span data-ttu-id="76508-156">Configurare il componente **gestore Risolutore (script)** :</span><span class="sxs-lookup"><span data-stu-id="76508-156">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="76508-157">Modificare il **tipo di destinazione rilevata** in **join a mano**</span><span class="sxs-lookup"><span data-stu-id="76508-157">Change **Tracked Target Type** to **Hand Joint**</span></span>
* <span data-ttu-id="76508-158">Modificare la **mano rilevata** a **destra**</span><span class="sxs-lookup"><span data-stu-id="76508-158">Change **Tracked Handness** to **Right**</span></span>
* <span data-ttu-id="76508-159">Modificare la **giunzione della mano registrata** fino al **polso**</span><span class="sxs-lookup"><span data-stu-id="76508-159">Change **Tracked Hand Joint** to **Wrist**</span></span>

<span data-ttu-id="76508-160">Configurare il componente **visualizzazione radiale (script)** :</span><span class="sxs-lookup"><span data-stu-id="76508-160">Configure the **Radial View (Script)** component:</span></span>

* <span data-ttu-id="76508-161">Modificare la **direzione di riferimento** in **orientata a oggetti**, quindi selezionare la casella di controllo **Orient to Reference Direction**</span><span class="sxs-lookup"><span data-stu-id="76508-161">Change **Reference Direction** to **Object Oriented**, then check the **Orient To Reference Direction** checkbox</span></span>
* <span data-ttu-id="76508-162">Modificare la distanza **minima** e la **distanza massima** con 0</span><span class="sxs-lookup"><span data-stu-id="76508-162">Change **Min Distance** and **Max Distance** to 0</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a><span data-ttu-id="76508-164">3. testare il Risolutore di viste radiali usando la simulazione in-Editor</span><span class="sxs-lookup"><span data-stu-id="76508-164">3. Test the Radial View Solver using the in-editor simulation</span></span>

<span data-ttu-id="76508-165">Premere il pulsante Riproduci per attivare la modalità di gioco e quindi tenere premuto la barra spaziatrice per visualizzare la mano.</span><span class="sxs-lookup"><span data-stu-id="76508-165">Press the Play button to enter Game mode and then press and hold the spacebar to bring up the hand.</span></span> <span data-ttu-id="76508-166">Spostare il cursore del mouse per spostare la mano, quindi fare clic e tenendo premuto il pulsante sinistro del mouse per ruotare la mano:</span><span class="sxs-lookup"><span data-stu-id="76508-166">Move the mouse cursor around to move the hand, and click and hold the left mouse button to rotate the hand:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a><span data-ttu-id="76508-168">Complimenti</span><span class="sxs-lookup"><span data-stu-id="76508-168">Congratulations</span></span>

<span data-ttu-id="76508-169">In questa esercitazione si è appreso come usare i resolver di MRTK per fare in modo che un'interfaccia utente segua in modo intuitivo l'utente.</span><span class="sxs-lookup"><span data-stu-id="76508-169">In this tutorial, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="76508-170">Si è inoltre appreso come alleghire un risolutore a un oggetto, ad esempio Cube, per seguire le mani rilevate dall'utente.</span><span class="sxs-lookup"><span data-stu-id="76508-170">You also learned how to attach a Solver to an object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="76508-171">Per ulteriori informazioni su questi e altri risolutori inclusi in MRTK, è possibile visitare la guida per i [risolutori](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="76508-171">To learn more about these and other solvers included with the MRTK,  you can visit the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="76508-172">Esercitazione successiva: 5. interazione con oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="76508-172">Next Tutorial: 5. Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)

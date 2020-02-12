---
title: Esercitazioni introduttive-5. Interazione con oggetti 3D
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: a1b26d56b4693ef23f2d77ba53e0961693489a3a
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2020
ms.locfileid: "77130282"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="89bfa-104">5. interazione con oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="89bfa-104">5. Interacting with 3D objects</span></span>

<span data-ttu-id="89bfa-105">In questa esercitazione si apprenderanno informazioni sul contenuto 3D di base e sull'esperienza utente, ad esempio l'organizzazione di oggetti 3D come parte di una raccolta, i riquadri per la manipolazione di base, l'interazione quasi e la distanza e i movimenti di tocco e di manipolazione con il rilevamento manuale.</span><span class="sxs-lookup"><span data-stu-id="89bfa-105">In this tutorial, you will learn about basic 3D content and user experience, such as organizing 3D objects as part of a collection, bounding boxes for basic manipulation, near and far interaction, and touch and grab gestures with hand tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="89bfa-106">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="89bfa-106">Objectives</span></span>

* <span data-ttu-id="89bfa-107">Creare un pannello di oggetti 3D che verrà usato per gli altri obiettivi di apprendimento</span><span class="sxs-lookup"><span data-stu-id="89bfa-107">Create a panel of 3D objects which will be used for the other learning objectives</span></span>
* <span data-ttu-id="89bfa-108">Implementare i cubi di delimitazione</span><span class="sxs-lookup"><span data-stu-id="89bfa-108">Implement bounding boxes</span></span>
* <span data-ttu-id="89bfa-109">Configurare gli oggetti 3D per la manipolazione di base, ad esempio spostare, ruotare e ridimensionare</span><span class="sxs-lookup"><span data-stu-id="89bfa-109">Configure 3D objects for basic manipulation such as move, rotate, and scale</span></span>
* <span data-ttu-id="89bfa-110">Esplorare l'interazione da vicino e da lontano</span><span class="sxs-lookup"><span data-stu-id="89bfa-110">Explore near and far interaction</span></span>
* <span data-ttu-id="89bfa-111">Informazioni sugli altri movimenti di rilevamento della mano, ad esempio la cattura e il tocco</span><span class="sxs-lookup"><span data-stu-id="89bfa-111">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="89bfa-112">Importazione delle risorse dell'esercitazione</span><span class="sxs-lookup"><span data-stu-id="89bfa-112">Importing the tutorial assets</span></span>

<span data-ttu-id="89bfa-113">Scaricare e importare il pacchetto personalizzato Unity:</span><span class="sxs-lookup"><span data-stu-id="89bfa-113">Download and import the Unity custom package:</span></span>

* [<span data-ttu-id="89bfa-114">MRTK. HoloLens2. Unity. Esercitations. assets. GettingStarted. 2.2.0.0. file unitypackage Tools</span><span class="sxs-lookup"><span data-stu-id="89bfa-114">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.2.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.0.unitypackage)

<span data-ttu-id="89bfa-115">Dopo aver importato le risorse dell'esercitazione, la finestra del progetto avrà un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="89bfa-115">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="89bfa-117">Per un promemoria su come importare un pacchetto personalizzato Unity, è possibile fare riferimento alle istruzioni [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) .</span><span class="sxs-lookup"><span data-stu-id="89bfa-117">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="decluttering-the-scene-view"></a><span data-ttu-id="89bfa-118">Disordine della visualizzazione scena</span><span class="sxs-lookup"><span data-stu-id="89bfa-118">Decluttering the scene view</span></span>

<span data-ttu-id="89bfa-119">Per semplificare l'uso della scena, impostare la **visibilità della scena** per il cubo e gli oggetti buttoncollection su off facendo clic sull'icona a forme di **occhio** a sinistra degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="89bfa-119">To make it easier to work with your scene, set the **scene visibility** for the Cube and ButtonCollection objects to off by clicking the **eye** icon to the left of the objects.</span></span> <span data-ttu-id="89bfa-120">In questo modo l'oggetto viene nascosto nella finestra della scena senza modificarne la visibilità nel gioco:</span><span class="sxs-lookup"><span data-stu-id="89bfa-120">This hides the object in the Scene window without changing their in-game visibility:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="89bfa-122">Per altre informazioni sui controlli di visibilità della scena e su come usarli per ottimizzare la visualizzazione scena e il flusso di lavoro, è possibile visitare la documentazione relativa alla <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">visibilità della scena</a> di Unity.</span><span class="sxs-lookup"><span data-stu-id="89bfa-122">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can visit Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

## <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="89bfa-123">Organizzazione di oggetti 3D in una raccolta</span><span class="sxs-lookup"><span data-stu-id="89bfa-123">Organizing 3D objects in a collection</span></span>

<span data-ttu-id="89bfa-124">In questa sezione verrà creato un pannello di oggetti 3D che verrà usato per esplorare varie modalità di interazione con gli oggetti 3D nelle sezioni seguenti di questa esercitazione.</span><span class="sxs-lookup"><span data-stu-id="89bfa-124">In this section, you will create a panel of 3D objects which you will use when exploring various ways of interacting with 3D objects in the following sections of this tutorial.</span></span> <span data-ttu-id="89bfa-125">In particolare, gli oggetti 3D verranno configurati in modo da essere posizionati in una griglia 3 x 3.</span><span class="sxs-lookup"><span data-stu-id="89bfa-125">Specifically, you will configure the 3D objects to be positioned on a 3 x 3 grid.</span></span>

<span data-ttu-id="89bfa-126">Analogamente a quando è [stato creato un pannello di pulsanti](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), i passaggi principali da eseguire sono:</span><span class="sxs-lookup"><span data-stu-id="89bfa-126">Similarly to when you [created a panel of buttons](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), the main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="89bfa-127">Padre degli oggetti 3D in un oggetto padre</span><span class="sxs-lookup"><span data-stu-id="89bfa-127">Parent the 3D objects to a parent object</span></span>
2. <span data-ttu-id="89bfa-128">Aggiungere e configurare il componente Grid Object Collection (script)</span><span class="sxs-lookup"><span data-stu-id="89bfa-128">Add and configure the Grid Object Collection (Script) component</span></span>

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a><span data-ttu-id="89bfa-129">1. padre degli oggetti 3D in un oggetto padre</span><span class="sxs-lookup"><span data-stu-id="89bfa-129">1. Parent the 3D objects to a parent object</span></span>

<span data-ttu-id="89bfa-130">Nella finestra gerarchia **creare un oggetto vuoto**, assegnargli un nome appropriato, ad esempio **3DObjectCollection**, e posizionarlo in una posizione appropriata, ad esempio X = 0, Y =-0,2, Z = 2.</span><span class="sxs-lookup"><span data-stu-id="89bfa-130">In the Hierarchy window, **create an empty object**, give it a suitable name, for example, **3DObjectCollection**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

<span data-ttu-id="89bfa-131">Nella finestra del progetto passare a **assets** > **MRTK. Tutorials. GettingStarted** > **prefabbricati** **, quindi i** prefabbricati seguenti in **3DObjectCollection**:</span><span class="sxs-lookup"><span data-stu-id="89bfa-131">In the Project window, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, then **Parent** the following prefabs to the **3DObjectCollection**:</span></span>

* <span data-ttu-id="89bfa-132">Cheese</span><span class="sxs-lookup"><span data-stu-id="89bfa-132">Cheese</span></span>
* <span data-ttu-id="89bfa-133">CoffeeCup</span><span class="sxs-lookup"><span data-stu-id="89bfa-133">CoffeeCup</span></span>
* <span data-ttu-id="89bfa-134">EarthCore</span><span class="sxs-lookup"><span data-stu-id="89bfa-134">EarthCore</span></span>
* <span data-ttu-id="89bfa-135">Octa</span><span class="sxs-lookup"><span data-stu-id="89bfa-135">Octa</span></span>
* <span data-ttu-id="89bfa-136">Platonico</span><span class="sxs-lookup"><span data-stu-id="89bfa-136">Platonic</span></span>
* <span data-ttu-id="89bfa-137">TheModule</span><span class="sxs-lookup"><span data-stu-id="89bfa-137">TheModule</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

<span data-ttu-id="89bfa-139">Nella finestra gerarchia **creare tre cubi** come oggetti figlio di **3DObjectCollection** e impostare la relativa **scala** di trasformazione su X = 0,15, Y = 0,15, Z = 0,15:</span><span class="sxs-lookup"><span data-stu-id="89bfa-139">In the Hierarchy window, **create three cubes** as a child objects of the **3DObjectCollection** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

<!-- TODO: Finish -->
> [!TIP]
> <span data-ttu-id="89bfa-141">Per un promemoria su come eseguire i passaggi elencati in precedenza, è possibile fare riferimento all'esercitazione relativa alla [creazione dell'interfaccia utente e alla configurazione del Toolkit di realtà mista](mrlearning-base-ch2.md) .</span><span class="sxs-lookup"><span data-stu-id="89bfa-141">For a reminder on how to do the steps listed above, you can refer to the [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md) tutorial.</span></span>

<span data-ttu-id="89bfa-142">Riposizionare i cubi in modo che sia possibile visualizzare ogni cubo:</span><span class="sxs-lookup"><span data-stu-id="89bfa-142">Reposition the cubes so you can see each cube:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

<span data-ttu-id="89bfa-144">Nella finestra del progetto passare a **assets** > **MixedRealityToolkit. SDK** > **StandardAssets** > **Materials** per visualizzare i materiali forniti con MRTK.</span><span class="sxs-lookup"><span data-stu-id="89bfa-144">In the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** to see materials provided with the MRTK.</span></span>

<span data-ttu-id="89bfa-145">**Fare clic su e trascinare** un materiale appropriato nella proprietà elemento 0 di **materiali** renderer mesh del cubo, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="89bfa-145">**Click-and-drag** a suitable material on to each cube's Mesh Renderer **Materials** Element 0 property, for example:</span></span>

* <span data-ttu-id="89bfa-146">MRTK_Standard_GlowingCyan</span><span class="sxs-lookup"><span data-stu-id="89bfa-146">MRTK_Standard_GlowingCyan</span></span>
* <span data-ttu-id="89bfa-147">MRTK_Standard_GlowingOrange</span><span class="sxs-lookup"><span data-stu-id="89bfa-147">MRTK_Standard_GlowingOrange</span></span>
* <span data-ttu-id="89bfa-148">MRTK_Standard_Green:</span><span class="sxs-lookup"><span data-stu-id="89bfa-148">MRTK_Standard_Green:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="89bfa-150">2. aggiungere e configurare il componente Grid Object Collection (script)</span><span class="sxs-lookup"><span data-stu-id="89bfa-150">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="89bfa-151">Aggiungere un componente **Grid Object Collection (script)** all'oggetto 3DObjectCollection e configurarlo come segue:</span><span class="sxs-lookup"><span data-stu-id="89bfa-151">Add a **Grid Object Collection (Script)** component to the 3DObjectCollection object, and configure it as follows:</span></span>

* <span data-ttu-id="89bfa-152">Modificare il **tipo di ordinamento** in ordine figlio per assicurarsi che gli oggetti figlio siano ordinati nell'ordine in cui sono stati inseriti nell'oggetto padre.</span><span class="sxs-lookup"><span data-stu-id="89bfa-152">Change **Sort Type** to Child Order to ensure the child objects are sorted in the order you have placed them under the parent object</span></span>

<span data-ttu-id="89bfa-153">Quindi fare clic sul pulsante **Aggiorna raccolta** per applicare la nuova configurazione:</span><span class="sxs-lookup"><span data-stu-id="89bfa-153">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a><span data-ttu-id="89bfa-155">Manipolazione di oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="89bfa-155">Manipulating 3D objects</span></span>

<span data-ttu-id="89bfa-156">In questa sezione verrà aggiunta la possibilità di modificare tutti gli oggetti 3D nel pannello creato nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="89bfa-156">In this section, you will add the ability to manipulate all the 3D objects in the panel you created in the previous section.</span></span> <span data-ttu-id="89bfa-157">Inoltre, per gli oggetti prefabbricati, si consentirà agli utenti di raggiungere e acquisire questi oggetti con le mani tracciate.</span><span class="sxs-lookup"><span data-stu-id="89bfa-157">Additionally, for the prefab objects, you will enable users to reach out and grab these objects with tracked hands.</span></span> <span data-ttu-id="89bfa-158">Si esamineranno quindi alcuni comportamenti di manipolazione che è possibile applicare agli oggetti.</span><span class="sxs-lookup"><span data-stu-id="89bfa-158">Then you will explore a few manipulation behaviors that you can apply to your objects.</span></span>

<span data-ttu-id="89bfa-159">Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:</span><span class="sxs-lookup"><span data-stu-id="89bfa-159">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="89bfa-160">Aggiungere il componente gestore modifiche (script) a tutti gli oggetti</span><span class="sxs-lookup"><span data-stu-id="89bfa-160">Add the Manipulation Handler (Script) component to all the objects</span></span>
2. <span data-ttu-id="89bfa-161">Aggiungere il componente near interactionable (script) a oggetti prefabbricati</span><span class="sxs-lookup"><span data-stu-id="89bfa-161">Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>
3. <span data-ttu-id="89bfa-162">Configurare il componente di gestione della manipolazione (script)</span><span class="sxs-lookup"><span data-stu-id="89bfa-162">Configure the Manipulation Handler (Script) component</span></span>

> [!IMPORTANT]
> <span data-ttu-id="89bfa-163">Per poter **modificare un oggetto**, l'oggetto deve disporre dei componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="89bfa-163">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="89bfa-164">Componente **Collider** , ad esempio, box Collider</span><span class="sxs-lookup"><span data-stu-id="89bfa-164">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="89bfa-165">Componente **gestione manipolazione (script)**</span><span class="sxs-lookup"><span data-stu-id="89bfa-165">**Manipulation Handler (Script)** component</span></span>
>
> <span data-ttu-id="89bfa-166">Per poter **modificare** e **acquisire un oggetto con le lancette rilevate**, l'oggetto deve disporre dei componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="89bfa-166">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="89bfa-167">Componente **Collider** , ad esempio, box Collider</span><span class="sxs-lookup"><span data-stu-id="89bfa-167">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="89bfa-168">Componente **gestione manipolazione (script)**</span><span class="sxs-lookup"><span data-stu-id="89bfa-168">**Manipulation Handler (Script)** component</span></span>
> * <span data-ttu-id="89bfa-169">Componente **near Interaction (script)**</span><span class="sxs-lookup"><span data-stu-id="89bfa-169">**Near Interaction Grabbable (Script)** component</span></span>

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a><span data-ttu-id="89bfa-170">1. aggiungere il componente gestore modifiche (script) a tutti gli oggetti</span><span class="sxs-lookup"><span data-stu-id="89bfa-170">1. Add the Manipulation Handler (Script) component to all the objects</span></span>

<span data-ttu-id="89bfa-171">Nella finestra gerarchia selezionare l'oggetto **Cheese** , tenere premuto il tasto **MAIUSC** , quindi selezionare l'oggetto **Cube ()** e aggiungere il componente **handler (script) di manipolazione** a tutti gli oggetti:</span><span class="sxs-lookup"><span data-stu-id="89bfa-171">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **Cube ()** object and add the **Manipulation Handler (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="89bfa-173">Ai fini di questa esercitazione, i Collider sono già stati aggiunti ai prefabbricati.</span><span class="sxs-lookup"><span data-stu-id="89bfa-173">For the purpose of this tutorial, colliders have already been added to the prefabs.</span></span> <span data-ttu-id="89bfa-174">Per le primitive Unity, ad esempio gli oggetti cubo, il componente Collider viene aggiunto automaticamente quando viene creato l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="89bfa-174">For Unity primitives, such as the Cube objects, the Collider component is automatically added when the object is created.</span></span> <span data-ttu-id="89bfa-175">Nell'immagine precedente, i Collider sono rappresentati dai profili verdi.</span><span class="sxs-lookup"><span data-stu-id="89bfa-175">In the image above, the colliders are represented by the green outlines.</span></span> <span data-ttu-id="89bfa-176">Per ulteriori informazioni sui Collider, è possibile visitare la documentazione di Unity <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> .</span><span class="sxs-lookup"><span data-stu-id="89bfa-176">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a><span data-ttu-id="89bfa-177">2. aggiungere il componente near Interaction (script) a oggetti prefabbricati</span><span class="sxs-lookup"><span data-stu-id="89bfa-177">2. Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>

<span data-ttu-id="89bfa-178">Nella finestra gerarchia selezionare l'oggetto **Cheese** , tenere premuto il tasto **MAIUSC** , quindi selezionare l'oggetto **TheModule** e aggiungere il componente **near interactionable (script)** a tutti gli oggetti:</span><span class="sxs-lookup"><span data-stu-id="89bfa-178">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **TheModule** object and add the **Near Interaction Grabbable (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a><span data-ttu-id="89bfa-180">3. configurare il componente di gestione della manipolazione (script)</span><span class="sxs-lookup"><span data-stu-id="89bfa-180">3. Configure the Manipulation Handler (Script) component</span></span>

#### <a name="default-manipulation"></a><span data-ttu-id="89bfa-181">Manipolazione predefinita</span><span class="sxs-lookup"><span data-stu-id="89bfa-181">Default manipulation</span></span>

<span data-ttu-id="89bfa-182">Per l'oggetto **cubo** , lasciare tutte le proprietà predefinite per verificare il comportamento di manipolazione predefinito:</span><span class="sxs-lookup"><span data-stu-id="89bfa-182">For the **Cube** object, leave all properties at default, to experience the default manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> <span data-ttu-id="89bfa-184">Per reimpostare i valori predefiniti di un componente, è possibile selezionare l'icona delle impostazioni del componente e selezionare Reimposta.</span><span class="sxs-lookup"><span data-stu-id="89bfa-184">To reset a component to its default values, you can select the component's Settings icon and select Reset.</span></span>

#### <a name="restrict-manipulation-to-scale-only"></a><span data-ttu-id="89bfa-185">Limitazione della manipolazione solo per la scalabilità</span><span class="sxs-lookup"><span data-stu-id="89bfa-185">Restrict manipulation to scale only</span></span>

<span data-ttu-id="89bfa-186">Per l'oggetto **Cube (1)** , modificare **due tipi di manipolazione gestiti** in scale in modo da consentire solo all'utente di modificare le dimensioni dell'oggetto:</span><span class="sxs-lookup"><span data-stu-id="89bfa-186">For the **Cube (1)** object, change **Two Handed Manipulation Type** to Scale to only allow the user to change the object's size:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a><span data-ttu-id="89bfa-188">Vincolare lo spostamento a una distanza fissa dall'utente</span><span class="sxs-lookup"><span data-stu-id="89bfa-188">Constrain the movement to a fixed distance from the user</span></span>

<span data-ttu-id="89bfa-189">Per l'oggetto **Cube (2)** , modificare il **vincolo on Movement** per correggere la distanza dall'Head in modo che, quando l'oggetto viene spostato, rimanga alla stessa distanza dall'utente:</span><span class="sxs-lookup"><span data-stu-id="89bfa-189">For the **Cube (2)** object, change **Constraint On Movement** to Fix Distance From Head so that when the object is moved, it stays at the same distance from the user:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a><span data-ttu-id="89bfa-191">Manipolazione predefinita</span><span class="sxs-lookup"><span data-stu-id="89bfa-191">Default grabbable manipulation</span></span>

<span data-ttu-id="89bfa-192">Per gli oggetti **Cheese**, **CoffeCup**e **EarthCore** , lasciare tutte le proprietà predefinite per poter provare il comportamento predefinito di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="89bfa-192">For the **Cheese**, **CoffeCup**, and **EarthCore** objects, leave all properties at default, to experience the default grabbable manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a><span data-ttu-id="89bfa-194">Rimuovere la capacità di manipolazione</span><span class="sxs-lookup"><span data-stu-id="89bfa-194">Remove the ability of far manipulation</span></span>

<span data-ttu-id="89bfa-195">Per l'oggetto **Octa** , deselezionare la casella di controllo **Consenti modifiche a lungo** per fare in modo che l'utente possa interagire direttamente con l'oggetto usando le mani rilevate:</span><span class="sxs-lookup"><span data-stu-id="89bfa-195">For the **Octa** object, uncheck the **Allow Far Manipulation** checkbox to make it so the user can only interact with the object directly using tracked hands:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a><span data-ttu-id="89bfa-197">Far ruotare un oggetto intorno al centro</span><span class="sxs-lookup"><span data-stu-id="89bfa-197">Make an object rotate around its center</span></span>

<span data-ttu-id="89bfa-198">Per l'oggetto **Platonic** modificare **una modalità di rotazione della mano vicino** a una modalità di rotazione della **mano** , per ruotare l'oggetto in modo da fare in modo che, quando l'utente ruota l'oggetto con una sola mano, ruoti intorno al centro dell'oggetto:</span><span class="sxs-lookup"><span data-stu-id="89bfa-198">For the **Platonic** object, change **One Hand Rotation Mode Near** and **One Hand Rotation Mode Far** to Rotate About Object Center to make it so when the user rotates the object with one hand, it rotates around the object's center:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="prevent-movement-after-object-is-released"></a><span data-ttu-id="89bfa-200">Impedisci spostamento dopo il rilascio dell'oggetto</span><span class="sxs-lookup"><span data-stu-id="89bfa-200">Prevent movement after object is released</span></span>

<span data-ttu-id="89bfa-201">Per l'oggetto **TheModule** , modificare il **comportamento della versione** in modo che, una volta rilasciato l'oggetto dall'utente, non continui a muoversi:</span><span class="sxs-lookup"><span data-stu-id="89bfa-201">For the **TheModule** object, change **Release Behavior** to Nothing so that once the object is released from the user's hand, it doesn’t continue to move:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

<span data-ttu-id="89bfa-203">Per ulteriori informazioni sul componente del gestore della manipolazione e sulle proprietà associate, è possibile visitare la guida del [gestore della manipolazione](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) nel portale della [documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="89bfa-203">To learn more about the Manipulation handler component and its associated properties, you can visit the [Manipulation handler](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="89bfa-204">Aggiunta di rettangoli di delimitazione</span><span class="sxs-lookup"><span data-stu-id="89bfa-204">Adding bounding boxes</span></span>

<span data-ttu-id="89bfa-205">I rettangoli di delimitazione rendono più semplice e intuitivo manipolare gli oggetti con una sola mano, sia per l'interazione vicina che per quella più lunga, fornendo handle che possono essere utilizzati per la scalabilità e la rotazione.</span><span class="sxs-lookup"><span data-stu-id="89bfa-205">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="89bfa-206">In questo esempio si aggiungerà un rettangolo di delimitazione all'oggetto EarthCore in modo che questo oggetto possa ora interagire con la manipolazione degli oggetti configurata nella sezione precedente, nonché ridimensionata e ruotata usando gli handle del rettangolo di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="89bfa-206">In this example, you will add a bounding box to the EarthCore object so this object can now be interacted with using the object manipulation you configured in the previous section, as well as, scaled and rotated using the bounding box handles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="89bfa-207">Per poter utilizzare un rettangolo di **delimitazione**, è necessario che nell'oggetto siano presenti i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="89bfa-207">To be able to use a **bounding box**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="89bfa-208">Componente **Collider** , ad esempio, box Collider</span><span class="sxs-lookup"><span data-stu-id="89bfa-208">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="89bfa-209">Componente del rettangolo di **delimitazione (script)**</span><span class="sxs-lookup"><span data-stu-id="89bfa-209">**Bounding Box (Script)** component</span></span>

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a><span data-ttu-id="89bfa-210">1. aggiungere il componente del rettangolo di delimitazione (script) all'oggetto EarthCore</span><span class="sxs-lookup"><span data-stu-id="89bfa-210">1. Add the Bounding Box (Script) component to the EarthCore object</span></span>

<span data-ttu-id="89bfa-211">Nella finestra di controllo selezionare l'oggetto **EarthCore** e aggiungere il componente **(script) del rettangolo** di selezione all'oggetto EarthCore:</span><span class="sxs-lookup"><span data-stu-id="89bfa-211">In the Inspector window, select the **EarthCore** object and add the **Bounding Box (Script)** component to the EarthCore object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> <span data-ttu-id="89bfa-213">Le visualizzazioni del rettangolo di delimitazione vengono create in fase di esecuzione e pertanto non sono visibili prima di passare alla modalità di gioco.</span><span class="sxs-lookup"><span data-stu-id="89bfa-213">The Bounding Box visualizations is created at run time and therefore not visible before you enter Game mode.</span></span>

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a><span data-ttu-id="89bfa-214">2. visualizzare e testare il rettangolo di delimitazione usando la simulazione in-Editor</span><span class="sxs-lookup"><span data-stu-id="89bfa-214">2. Visualize and test the bounding box using the in-editor simulation</span></span>

<span data-ttu-id="89bfa-215">Premere il pulsante Riproduci per attivare la modalità di gioco.</span><span class="sxs-lookup"><span data-stu-id="89bfa-215">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="89bfa-216">Quindi tenere premuto la barra spaziatrice per visualizzare la mano e usare il mouse per interagire con il rettangolo di delimitazione:</span><span class="sxs-lookup"><span data-stu-id="89bfa-216">Then press and hold the spacebar to bring up the hand and use the mouse to interact with the bounding box:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

<span data-ttu-id="89bfa-218">Per ulteriori informazioni sul componente del riquadro e sulle proprietà associate, è possibile visitare la guida del rettangolo di [delimitazione](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="89bfa-218">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-touch-effects"></a><span data-ttu-id="89bfa-219">Aggiunta degli effetti tocco</span><span class="sxs-lookup"><span data-stu-id="89bfa-219">Adding touch effects</span></span>

<span data-ttu-id="89bfa-220">In questo esempio verranno abilitati gli eventi da attivare quando si tocca un oggetto con la mano.</span><span class="sxs-lookup"><span data-stu-id="89bfa-220">In this example, you will enable events to be triggered when you touch an object with your hand.</span></span> <span data-ttu-id="89bfa-221">In particolare, l'oggetto Octa verrà configurato per riprodurre un effetto acustico quando l'utente lo tocca.</span><span class="sxs-lookup"><span data-stu-id="89bfa-221">Specifically, you will configure the Octa object to play a sound effect when the user touches it.</span></span>

<span data-ttu-id="89bfa-222">Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:</span><span class="sxs-lookup"><span data-stu-id="89bfa-222">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="89bfa-223">Aggiungere un componente di origine audio all'oggetto</span><span class="sxs-lookup"><span data-stu-id="89bfa-223">Add an Audio Source component to the object</span></span>
2. <span data-ttu-id="89bfa-224">Aggiungere il componente near Interaction (script) per l'interazione all'oggetto</span><span class="sxs-lookup"><span data-stu-id="89bfa-224">Add the Near Interaction Touchable (Script) component to the object</span></span>
3. <span data-ttu-id="89bfa-225">Aggiungere il componente tocco interazione mano (script) all'oggetto</span><span class="sxs-lookup"><span data-stu-id="89bfa-225">Add the Hand Interaction Touch (Script) component to the object</span></span>
4. <span data-ttu-id="89bfa-226">Implementare l'evento on touch Started</span><span class="sxs-lookup"><span data-stu-id="89bfa-226">Implement the On Touch Started event</span></span>
5. <span data-ttu-id="89bfa-227">Testare l'interazione con il tocco usando la simulazione in-Editor</span><span class="sxs-lookup"><span data-stu-id="89bfa-227">Test the touch interaction using the in-editor simulation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="89bfa-228">Per poter **attivare gli eventi di tocco**, l'oggetto deve disporre dei componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="89bfa-228">To be able to **trigger touch events**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="89bfa-229">Componente **Collider** , preferibilmente box Collider</span><span class="sxs-lookup"><span data-stu-id="89bfa-229">**Collider** component, preferably a Box Collider</span></span>
> * <span data-ttu-id="89bfa-230">Componente **near Interaction touchable (script)**</span><span class="sxs-lookup"><span data-stu-id="89bfa-230">**Near Interaction Touchable (Script)** component</span></span>
> * <span data-ttu-id="89bfa-231">Componente **tocco interazione mano (script)**</span><span class="sxs-lookup"><span data-stu-id="89bfa-231">**Hand Interaction Touch (Script)** component</span></span>

> [!NOTE]
> <span data-ttu-id="89bfa-232">Il componente script (Hand Interaction touch) non fa parte di MRTK.</span><span class="sxs-lookup"><span data-stu-id="89bfa-232">The Hand Interaction Touch (Script) component is not part of MRTK.</span></span> <span data-ttu-id="89bfa-233">È stato importato con le risorse di questa esercitazione ed è stato originariamente incluso negli esempi di Unity Toolkit MixedReality.</span><span class="sxs-lookup"><span data-stu-id="89bfa-233">It was imported with this tutorial's assets and originally part of the MixedReality Toolkit Unity Examples.</span></span>

### <a name="1-add-an-audio-source-component-to-the-object"></a><span data-ttu-id="89bfa-234">1. aggiungere un componente di origine audio all'oggetto</span><span class="sxs-lookup"><span data-stu-id="89bfa-234">1. Add an Audio Source component to the object</span></span>

<span data-ttu-id="89bfa-235">Nella finestra gerarchia selezionare l'oggetto **Octa** , aggiungere un componente di **origine audio** all'oggetto OCTA e quindi modificare **Blend spaziale** in 1 per abilitare l'audio spaziale:</span><span class="sxs-lookup"><span data-stu-id="89bfa-235">In the Hierarchy window, select the **Octa** object, add an **Audio Source** component to the Octa object, and then change **Spatial Blend** to 1 to enable spatial audio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a><span data-ttu-id="89bfa-237">2. aggiungere il componente di prossimità interazione (script) per l'oggetto</span><span class="sxs-lookup"><span data-stu-id="89bfa-237">2. Add the Near Interaction Touchable (Script) component to the object</span></span>

<span data-ttu-id="89bfa-238">Se l'oggetto **Octa** è ancora selezionato, aggiungere il componente **near Interaction (script)** per l'oggetto Octa, quindi fare clic sui pulsanti **Correggi limiti** e **Correggi centro** per aggiornare le proprietà del centro locale e dei limiti di near Interaction touchable (script) in modo che corrispondano a BoxCollider:</span><span class="sxs-lookup"><span data-stu-id="89bfa-238">With the **Octa** object still selected, add the **Near Interaction Touchable (Script)** component to the Octa object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a><span data-ttu-id="89bfa-240">3. aggiungere il componente script (Hand Interaction touch) all'oggetto</span><span class="sxs-lookup"><span data-stu-id="89bfa-240">3. Add the Hand Interaction Touch (Script) component to the object</span></span>

<span data-ttu-id="89bfa-241">Con l'oggetto **Octa** ancora selezionato, aggiungere il componente **script (Hand Interaction touch)** all'oggetto Octa:</span><span class="sxs-lookup"><span data-stu-id="89bfa-241">With the **Octa** object still selected, add the **Hand Interaction Touch (Script)** component to the Octa object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a><span data-ttu-id="89bfa-243">4. implementare l'evento on touch Started</span><span class="sxs-lookup"><span data-stu-id="89bfa-243">4. Implement the On Touch Started event</span></span>

<span data-ttu-id="89bfa-244">Sul componente tocco interazione mano (script), fare clic sull'icona del piccolo **+** per creare un nuovo evento per **tocco avviato ()** .</span><span class="sxs-lookup"><span data-stu-id="89bfa-244">On the Hand Interaction Touch (Script) component, click the small **+** icon to create a new **On Touch Started ()** event.</span></span> <span data-ttu-id="89bfa-245">Configurare quindi l'oggetto **Octa** per ricevere l'evento e definire **audiosource. PlayOneShot** come azione da attivare:</span><span class="sxs-lookup"><span data-stu-id="89bfa-245">Then configure the **Octa** object to receive the event and define **AudioSource.PlayOneShot** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

<span data-ttu-id="89bfa-247">Passare a **asset** > **MixedRealityToolkit. SDK** > **StandardAssets** > Materials per visualizzare le clip audio fornite con MRTK e quindi assegnare una clip audio adatta al campo **clip** audio, ad esempio il clip audio MRTK_Gem:</span><span class="sxs-lookup"><span data-stu-id="89bfa-247">Navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > Materials to see audio clips provided with the MRTK, and then assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> <span data-ttu-id="89bfa-249">Per un promemoria su come implementare gli eventi, è possibile fare riferimento alle istruzioni per i [movimenti di rilevamento della mano e i pulsanti interagiscono](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) .</span><span class="sxs-lookup"><span data-stu-id="89bfa-249">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a><span data-ttu-id="89bfa-250">5. testare l'interazione con il tocco usando la simulazione in-Editor</span><span class="sxs-lookup"><span data-stu-id="89bfa-250">5. Test the touch interaction using the in-editor simulation</span></span>

<span data-ttu-id="89bfa-251">Premere il pulsante Riproduci per attivare la modalità di gioco.</span><span class="sxs-lookup"><span data-stu-id="89bfa-251">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="89bfa-252">Quindi tenere premuto la barra spaziatrice per visualizzare la mano e usare il mouse per toccare l'oggetto OCTA e attivare l'effetto audio:</span><span class="sxs-lookup"><span data-stu-id="89bfa-252">Then press and hold the spacebar to bring up the hand and use the mouse to touch the Octa object and trigger the sound effect:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> <span data-ttu-id="89bfa-254">Come è stato osservato durante il test dell'interazione del tocco e come illustrato nell'immagine precedente, il colore dell'oggetto Octa pulsava durante il suo tocco.</span><span class="sxs-lookup"><span data-stu-id="89bfa-254">As you saw when testing the touch interaction, and as shown in the image above, the Octa object color pulsated while it was touched.</span></span> <span data-ttu-id="89bfa-255">Questo effetto è hardcoded nel componente tocco interazione mano (script) e non è il risultato della configurazione degli eventi completata nei passaggi precedenti.</span><span class="sxs-lookup"><span data-stu-id="89bfa-255">This effect is hard coded into the Hand Interaction Touch (Script) component and not a result of the event configuration you completed in the steps above.</span></span>
>
> <span data-ttu-id="89bfa-256">Se si vuole disabilitare questo effetto, è possibile, ad esempio, impostare come commento o la riga 32' TargetRenderer = GetComponentInChildren<Renderer>();' che restituirà il valore null rimanente di TargetRenderer e il colore non pulsa.</span><span class="sxs-lookup"><span data-stu-id="89bfa-256">If you want to disable this effect, you can, for example, comment out or line 32 'TargetRenderer = GetComponentInChildren<Renderer>();' which will result in the TargetRenderer remaining null and the color not pulsating.</span></span>

## <a name="congratulations"></a><span data-ttu-id="89bfa-257">Complimenti</span><span class="sxs-lookup"><span data-stu-id="89bfa-257">Congratulations</span></span>

<span data-ttu-id="89bfa-258">In questa esercitazione si è appreso come organizzare gli oggetti 3D in una raccolta di griglie e come manipolare questi oggetti (ridimensionamento, rotazione e movimento) usando near Interaction (cattura diretta con le mani rilevate) e un'interazione di gran lunga (usando raggi di sguardi o raggi mano).</span><span class="sxs-lookup"><span data-stu-id="89bfa-258">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate these objects (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="89bfa-259">Si è inoltre appreso come inserire le caselle di delimitazione intorno agli oggetti 3D e come usare e personalizzare gli handle nei rettangoli di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="89bfa-259">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the handles on the bounding boxes.</span></span> <span data-ttu-id="89bfa-260">Hai infine appreso come attivare eventi nel momento in cui viene toccato un oggetto.</span><span class="sxs-lookup"><span data-stu-id="89bfa-260">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="89bfa-261">Lezione successiva: 6. esplorazione delle opzioni di input avanzate</span><span class="sxs-lookup"><span data-stu-id="89bfa-261">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)

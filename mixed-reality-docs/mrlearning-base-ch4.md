---
title: Esercitazioni introduttive - 5. Interazione con oggetti 3D
description: Informazioni sul contenuto 3D e sulle esperienze utente di base, ad esempio l'organizzazione di oggetti 3D e cubi di delimitazione per la manipolazione di base.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: b807ac7e51e4009d2c44d3b7c67fbdf3488ccbd9
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604992"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="2f553-105">5. Interazione con oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="2f553-105">5. Interacting with 3D objects</span></span>

<span data-ttu-id="2f553-106">In questa esercitazione troverai informazioni sul contenuto 3D e sull'esperienza utente di base (ad esempio, l'organizzazione degli oggetti 3D come parte di una raccolta), sui cubi di delimitazione per la manipolazione di base, sull'interazione da vicino e da lontano e sui movimenti per toccare e afferrare con il tracciamento della mano.</span><span class="sxs-lookup"><span data-stu-id="2f553-106">In this tutorial, you will learn about basic 3D content and user experience, such as organizing 3D objects as part of a collection, bounding boxes for basic manipulation, near and far interaction, and touch and grab gestures with hand tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="2f553-107">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="2f553-107">Objectives</span></span>

* <span data-ttu-id="2f553-108">Creare un pannello di oggetti 3D da usare per gli altri obiettivi di apprendimento</span><span class="sxs-lookup"><span data-stu-id="2f553-108">Create a panel of 3D objects which will be used for the other learning objectives</span></span>
* <span data-ttu-id="2f553-109">Implementare i cubi di delimitazione</span><span class="sxs-lookup"><span data-stu-id="2f553-109">Implement bounding boxes</span></span>
* <span data-ttu-id="2f553-110">Configurare oggetti 3D per la manipolazione di base, ad esempio spostare, ruotare e ridimensionare</span><span class="sxs-lookup"><span data-stu-id="2f553-110">Configure 3D objects for basic manipulation such as move, rotate, and scale</span></span>
* <span data-ttu-id="2f553-111">Esplorare l'interazione da vicino e da lontano</span><span class="sxs-lookup"><span data-stu-id="2f553-111">Explore near and far interaction</span></span>
* <span data-ttu-id="2f553-112">Apprendere altri movimenti di tracciamento della mano, come afferrare e toccare</span><span class="sxs-lookup"><span data-stu-id="2f553-112">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="2f553-113">Importazione degli asset dell'esercitazione</span><span class="sxs-lookup"><span data-stu-id="2f553-113">Importing the tutorial assets</span></span>

<span data-ttu-id="2f553-114">Scarica e importa il pacchetto personalizzato di Unity:</span><span class="sxs-lookup"><span data-stu-id="2f553-114">Download and import the Unity custom package:</span></span>

* [<span data-ttu-id="2f553-115">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="2f553-115">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)

<span data-ttu-id="2f553-116">Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="2f553-116">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="2f553-118">Per rivedere la procedura di importazione di un pacchetto personalizzato di Unity, puoi fare riferimento alle istruzioni contenute in [Importare Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="2f553-118">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="decluttering-the-scene-view"></a><span data-ttu-id="2f553-119">Rendere più chiara la vista della scena</span><span class="sxs-lookup"><span data-stu-id="2f553-119">Decluttering the scene view</span></span>

<span data-ttu-id="2f553-120">Per rendere più agevole l'uso della scena, disattiva la **visibilità** per gli oggetti **Cube** e **ButtonCollection** facendo clic sull'icona a forma di **occhio** a sinistra degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="2f553-120">To make it easier to work with your scene, set the **scene visibility** for the **Cube** and **ButtonCollection** objects to off by clicking the **eye** icon to the left of the objects.</span></span> <span data-ttu-id="2f553-121">In questo modo l'oggetto viene nascosto nella finestra Scene (Scena) senza effetti sulla sua visibilità nel gioco:</span><span class="sxs-lookup"><span data-stu-id="2f553-121">This hides the object in the Scene window without changing their in-game visibility:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="2f553-123">Per altre informazioni sui controlli per la visibilità nella scena e su come usarli per ottimizzare la vista e il flusso di lavoro della scena, puoi visitare la documentazione <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">corrispondente</a> di Unity.</span><span class="sxs-lookup"><span data-stu-id="2f553-123">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can visit Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

## <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="2f553-124">Organizzazione di oggetti 3D in una raccolta</span><span class="sxs-lookup"><span data-stu-id="2f553-124">Organizing 3D objects in a collection</span></span>

<span data-ttu-id="2f553-125">In questa sezione creerai un pannello di oggetti 3D che verrà usato per esplorare varie modalità di interazione con gli oggetti 3D nelle sezioni seguenti di questa esercitazione.</span><span class="sxs-lookup"><span data-stu-id="2f553-125">In this section, you will create a panel of 3D objects which you will use when exploring various ways of interacting with 3D objects in the following sections of this tutorial.</span></span> <span data-ttu-id="2f553-126">Più specificamente, configurerai gli oggetti 3D per il posizionamento in una griglia 3 x 3.</span><span class="sxs-lookup"><span data-stu-id="2f553-126">Specifically, you will configure the 3D objects to be positioned on a 3 x 3 grid.</span></span>

<span data-ttu-id="2f553-127">Come nella procedura usata per [creare in precedenza un pannello di pulsanti](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), i passaggi principali da eseguire sono:</span><span class="sxs-lookup"><span data-stu-id="2f553-127">Similarly to when you [created a panel of buttons](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), the main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="2f553-128">Associare gli oggetti 3D a un oggetto padre</span><span class="sxs-lookup"><span data-stu-id="2f553-128">Parent the 3D objects to a parent object</span></span>
2. <span data-ttu-id="2f553-129">Aggiungere e configurare il componente Grid Object Collection (Script) (Raccolta oggetti griglia - Script)</span><span class="sxs-lookup"><span data-stu-id="2f553-129">Add and configure the Grid Object Collection (Script) component</span></span>

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a><span data-ttu-id="2f553-130">1. Associare gli oggetti 3D a un oggetto padre</span><span class="sxs-lookup"><span data-stu-id="2f553-130">1. Parent the 3D objects to a parent object</span></span>

<span data-ttu-id="2f553-131">Nella finestra Hierarchy (Gerarchia) **crea un oggetto vuoto**, assegnagli un nome appropriato, ad esempio **3DObjectCollection**, e collocalo in una posizione adatta, ad esempio X = 0, Y = -0.2, Z = 2.</span><span class="sxs-lookup"><span data-stu-id="2f553-131">In the Hierarchy window, **create an empty object**, give it a suitable name, for example, **3DObjectCollection**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

<span data-ttu-id="2f553-132">Nella finestra Project (Progetto) passa ad **Assets** (Asset) > **MRTK.Tutorials.GettingStarted** > **Prefabs** (Prefab) e quindi **associa** a **3DObjectCollection** i prefab seguenti:</span><span class="sxs-lookup"><span data-stu-id="2f553-132">In the Project window, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, then **parent** the following prefabs to the **3DObjectCollection**:</span></span>

* <span data-ttu-id="2f553-133">Cheese</span><span class="sxs-lookup"><span data-stu-id="2f553-133">Cheese</span></span>
* <span data-ttu-id="2f553-134">CoffeeCup</span><span class="sxs-lookup"><span data-stu-id="2f553-134">CoffeeCup</span></span>
* <span data-ttu-id="2f553-135">EarthCore</span><span class="sxs-lookup"><span data-stu-id="2f553-135">EarthCore</span></span>
* <span data-ttu-id="2f553-136">Octa</span><span class="sxs-lookup"><span data-stu-id="2f553-136">Octa</span></span>
* <span data-ttu-id="2f553-137">Platonic</span><span class="sxs-lookup"><span data-stu-id="2f553-137">Platonic</span></span>
* <span data-ttu-id="2f553-138">TheModule</span><span class="sxs-lookup"><span data-stu-id="2f553-138">TheModule</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

<span data-ttu-id="2f553-140">Nella finestra Hierarchy (Gerarchia) **crea tre cubi** come oggetti figlio di **3DObjectCollection** e in Transform (Trasformazione) imposta **Scale** (Scala) su X = 0.15, Y = 0.15, Z = 0.15.</span><span class="sxs-lookup"><span data-stu-id="2f553-140">In the Hierarchy window, **create three cubes** as a child objects of the **3DObjectCollection** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="2f553-142">Per rivedere come eseguire i passaggi sopra indicati, puoi fare riferimento all'esercitazione [Creazione dell'interfaccia utente e configurazione di Mixed Reality Toolkit](mrlearning-base-ch2.md).</span><span class="sxs-lookup"><span data-stu-id="2f553-142">For a reminder on how to do the steps listed above, you can refer to the [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md) tutorial.</span></span>

<span data-ttu-id="2f553-143">Riposiziona i cubi in modo che sia possibile visualizzarli tutti:</span><span class="sxs-lookup"><span data-stu-id="2f553-143">Reposition the cubes so you can see each cube:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

<span data-ttu-id="2f553-145">Nella finestra Project (Progetto) passa ad **Assets** (Asset) > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** (Materiali) per visualizzare i materiali forniti con MRTK.</span><span class="sxs-lookup"><span data-stu-id="2f553-145">In the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** to see materials provided with the MRTK.</span></span>

<span data-ttu-id="2f553-146">**Fai clic e trascina** un materiale appropriato sulla proprietà Element 0 (Elemento 0) in **Materials** (Materiali) nella sezione Mesh Renderer (Renderer mesh) di ogni cubo, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="2f553-146">**Click-and-drag** a suitable material on to each cube's Mesh Renderer **Materials** Element 0 property, for example:</span></span>

* <span data-ttu-id="2f553-147">MRTK_Standard_GlowingCyan</span><span class="sxs-lookup"><span data-stu-id="2f553-147">MRTK_Standard_GlowingCyan</span></span>
* <span data-ttu-id="2f553-148">MRTK_Standard_GlowingOrange</span><span class="sxs-lookup"><span data-stu-id="2f553-148">MRTK_Standard_GlowingOrange</span></span>
* <span data-ttu-id="2f553-149">MRTK_Standard_Green</span><span class="sxs-lookup"><span data-stu-id="2f553-149">MRTK_Standard_Green</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="2f553-151">2. Aggiungere e configurare il componente Grid Object Collection (Script) (Raccolta oggetti griglia - Script)</span><span class="sxs-lookup"><span data-stu-id="2f553-151">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="2f553-152">Aggiungi un componente **Grid Object Collection (Script)** (Raccolta oggetti griglia - Script) all'oggetto **3DObjectCollection** e configuralo come segue:</span><span class="sxs-lookup"><span data-stu-id="2f553-152">Add a **Grid Object Collection (Script)** component to the **3DObjectCollection** object, and configure it as follows:</span></span>

* <span data-ttu-id="2f553-153">Imposta **Sort Type** (Tipo ordinamento) su **Child Order** (Ordine figlio) per assicurarti che gli oggetti figlio vengano ordinati in base alla sequenza in cui li hai posizionati sotto l'oggetto padre</span><span class="sxs-lookup"><span data-stu-id="2f553-153">Change **Sort Type** to **Child Order** to ensure the child objects are sorted in the order you have placed them under the parent object</span></span>

<span data-ttu-id="2f553-154">Fai quindi clic sul pulsante **Update Collection** (Aggiorna raccolta) per applicare la nuova configurazione:</span><span class="sxs-lookup"><span data-stu-id="2f553-154">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a><span data-ttu-id="2f553-156">Manipolazione di oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="2f553-156">Manipulating 3D objects</span></span>

<span data-ttu-id="2f553-157">In questa sezione aggiungerai la possibilità di manipolare tutti gli oggetti 3D nel pannello creato nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="2f553-157">In this section, you will add the ability to manipulate all the 3D objects in the panel you created in the previous section.</span></span> <span data-ttu-id="2f553-158">Inoltre, per gli oggetti prefab, consentirai agli utenti di afferrare tali oggetti con le mani tracciate.</span><span class="sxs-lookup"><span data-stu-id="2f553-158">Additionally, for the prefab objects, you will enable users to reach out and grab these objects with tracked hands.</span></span> <span data-ttu-id="2f553-159">Potrai quindi esplorare alcuni comportamenti di manipolazione applicabili agli oggetti.</span><span class="sxs-lookup"><span data-stu-id="2f553-159">Then you will explore a few manipulation behaviors that you can apply to your objects.</span></span>

<span data-ttu-id="2f553-160">Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:</span><span class="sxs-lookup"><span data-stu-id="2f553-160">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="2f553-161">Aggiungere il componente Manipulation Handler (Script) (Gestore manipolazione - Script) a tutti gli oggetti</span><span class="sxs-lookup"><span data-stu-id="2f553-161">Add the Manipulation Handler (Script) component to all the objects</span></span>
2. <span data-ttu-id="2f553-162">Aggiungere il componente Near Interaction Grabbable (Script) (Afferrabile con interazione da vicino - Script) agli oggetti prefab</span><span class="sxs-lookup"><span data-stu-id="2f553-162">Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>
3. <span data-ttu-id="2f553-163">Configurare il componente Manipulation Handler (Script) (Gestore manipolazione - Script)</span><span class="sxs-lookup"><span data-stu-id="2f553-163">Configure the Manipulation Handler (Script) component</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2f553-164">Per poter **manipolare un oggetto**, è necessario che l'oggetto abbia i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="2f553-164">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="2f553-165">Componente **Collider** (Collisore), ad esempio un collisore cuboide</span><span class="sxs-lookup"><span data-stu-id="2f553-165">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="2f553-166">Componente **Manipulation Handler (Script)** (Gestore manipolazione - Script)</span><span class="sxs-lookup"><span data-stu-id="2f553-166">**Manipulation Handler (Script)** component</span></span>
>
> <span data-ttu-id="2f553-167">Per poter **manipolare** e **afferrare un oggetto con le mani tracciate**, è necessario che l'oggetto abbia i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="2f553-167">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="2f553-168">Componente **Collider** (Collisore), ad esempio un collisore cuboide</span><span class="sxs-lookup"><span data-stu-id="2f553-168">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="2f553-169">Componente **Manipulation Handler (Script)** (Gestore manipolazione - Script)</span><span class="sxs-lookup"><span data-stu-id="2f553-169">**Manipulation Handler (Script)** component</span></span>
> * <span data-ttu-id="2f553-170">Componente **Near Interaction Grabbable (Script)** (Afferrabile con interazione da vicino - Script)</span><span class="sxs-lookup"><span data-stu-id="2f553-170">**Near Interaction Grabbable (Script)** component</span></span>

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a><span data-ttu-id="2f553-171">1. Aggiungere il componente Manipulation Handler (Script) (Gestore manipolazione - Script) a tutti gli oggetti</span><span class="sxs-lookup"><span data-stu-id="2f553-171">1. Add the Manipulation Handler (Script) component to all the objects</span></span>

<span data-ttu-id="2f553-172">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Cheese**, tieni premuto **MAIUSC** e seleziona l'oggetto **Cube (2)** , quindi aggiungi il componente **Manipulation Handler (Script)** (Gestore manipolazione - Script) a tutti gli oggetti:</span><span class="sxs-lookup"><span data-stu-id="2f553-172">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **Cube () 2** object and add the **Manipulation Handler (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="2f553-174">Ai fini di questa esercitazione, i collisori sono già stati aggiunti ai prefab.</span><span class="sxs-lookup"><span data-stu-id="2f553-174">For the purpose of this tutorial, colliders have already been added to the prefabs.</span></span> <span data-ttu-id="2f553-175">Per i primitivi di Unity, quali gli oggetti Cube, il componente Collider (Collisore) viene aggiunto automaticamente quando viene creato l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="2f553-175">For Unity primitives, such as the Cube objects, the Collider component is automatically added when the object is created.</span></span> <span data-ttu-id="2f553-176">Nell'immagine precedente i collisori sono rappresentati dai contorni verdi.</span><span class="sxs-lookup"><span data-stu-id="2f553-176">In the image above, the colliders are represented by the green outlines.</span></span> <span data-ttu-id="2f553-177">Per altre informazioni sui collisori, puoi visitare la documentazione <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">corrispondente</a> di Unity.</span><span class="sxs-lookup"><span data-stu-id="2f553-177">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a><span data-ttu-id="2f553-178">2. Aggiungere il componente Near Interaction Grabbable (Script) (Afferrabile con interazione da vicino - Script) agli oggetti prefab</span><span class="sxs-lookup"><span data-stu-id="2f553-178">2. Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>

<span data-ttu-id="2f553-179">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Cheese**, tieni premuto **MAIUSC** e seleziona l'oggetto **TheModule**, quindi aggiungi il componente **Near Interaction Grabbable (Script)** (Afferrabile con interazione da vicino - Script) a tutti gli oggetti:</span><span class="sxs-lookup"><span data-stu-id="2f553-179">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **TheModule** object and add the **Near Interaction Grabbable (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a><span data-ttu-id="2f553-181">3. Configurare il componente Manipulation Handler (Script) (Gestore manipolazione - Script)</span><span class="sxs-lookup"><span data-stu-id="2f553-181">3. Configure the Manipulation Handler (Script) component</span></span>

#### <a name="default-manipulation"></a><span data-ttu-id="2f553-182">Manipolazione predefinita</span><span class="sxs-lookup"><span data-stu-id="2f553-182">Default manipulation</span></span>

<span data-ttu-id="2f553-183">Per l'oggetto **Cube**, lascia tutte le proprietà impostate sui rispettivi valori predefiniti per provare il comportamento di manipolazione predefinito:</span><span class="sxs-lookup"><span data-stu-id="2f553-183">For the **Cube** object, leave all properties at default, to experience the default manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> <span data-ttu-id="2f553-185">Per reimpostare un componente sui valori predefiniti, puoi fare clic sull'icona delle impostazioni del componente e quindi su Reset (Reimposta).</span><span class="sxs-lookup"><span data-stu-id="2f553-185">To reset a component to its default values, you can select the component's Settings icon and select Reset.</span></span>

#### <a name="restrict-manipulation-to-scale-only"></a><span data-ttu-id="2f553-186">Limitare la manipolazione al solo ridimensionamento</span><span class="sxs-lookup"><span data-stu-id="2f553-186">Restrict manipulation to scale only</span></span>

<span data-ttu-id="2f553-187">Per l'oggetto **Cube (1)** , imposta **Two Handed Manipulation Type** (Tipo di manipolazione con due mani) su **Scale** (Scala) per consentire all'utente solo di modificare le dimensioni dell'oggetto:</span><span class="sxs-lookup"><span data-stu-id="2f553-187">For the **Cube (1)** object, change **Two Handed Manipulation Type** to **Scale** to only allow the user to change the object's size:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a><span data-ttu-id="2f553-189">Vincolare lo spostamento a una distanza fissa dall'utente</span><span class="sxs-lookup"><span data-stu-id="2f553-189">Constrain the movement to a fixed distance from the user</span></span>

<span data-ttu-id="2f553-190">Per l'oggetto **Cube (2)** , imposta **Constraint On Movement** (Vincolo sullo spostamento) su **Fix Distance From Head** (Correggi distanza dalla testa) in modo che, se spostato, l'oggetto rimanga alla stessa distanza dall'utente:</span><span class="sxs-lookup"><span data-stu-id="2f553-190">For the **Cube (2)** object, change **Constraint On Movement** to **Fix Distance From Head** so that when the object is moved, it stays at the same distance from the user:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a><span data-ttu-id="2f553-192">Manipolazione afferrabile predefinita</span><span class="sxs-lookup"><span data-stu-id="2f553-192">Default grabbable manipulation</span></span>

<span data-ttu-id="2f553-193">Per gli oggetti **Cheese**, **CoffeCup** e **EarthCore**, lascia tutte le proprietà impostate sui rispettivi valori predefiniti per provare il comportamento di manipolazione afferrabile predefinito:</span><span class="sxs-lookup"><span data-stu-id="2f553-193">For the **Cheese**, **CoffeCup**, and **EarthCore** objects, leave all properties at default, to experience the default grabbable manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a><span data-ttu-id="2f553-195">Rimuovere la capacità di manipolazione da lontano</span><span class="sxs-lookup"><span data-stu-id="2f553-195">Remove the ability of far manipulation</span></span>

<span data-ttu-id="2f553-196">Per l'oggetto **Octa**, deseleziona la casella di controllo **Allow Far Manipulation** (Consenti manipolazione da lontano) in modo che l'utente possa interagire con l'oggetto solo direttamente usando le mani tracciate:</span><span class="sxs-lookup"><span data-stu-id="2f553-196">For the **Octa** object, un-check the **Allow Far Manipulation** checkbox to make it so the user can only interact with the object directly using tracked hands:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a><span data-ttu-id="2f553-198">Far ruotare un oggetto intorno al centro</span><span class="sxs-lookup"><span data-stu-id="2f553-198">Make an object rotate around its center</span></span>

<span data-ttu-id="2f553-199">Per l'oggetto **Platonic**, imposta **One Hand Rotation Mode Near** (Modalità di rotazione con una mano - Da vicino) e **One Hand Rotation Mode Far** (Modalità di rotazione con una mano - Da lontano) su **Rotate About Object Center** (Rotazione intorno al centro dell'oggetto) in modo che, quando l'utente ruota l'oggetto con una mano, questo ruoti intorno al suo centro:</span><span class="sxs-lookup"><span data-stu-id="2f553-199">For the **Platonic** object, change **One Hand Rotation Mode Near** and **One Hand Rotation Mode Far** to **Rotate About Object Center** to make it so when the user rotates the object with one hand, it rotates around the object's center:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a><span data-ttu-id="2f553-201">Mantenere lo spostamento dopo il rilascio dell'oggetto</span><span class="sxs-lookup"><span data-stu-id="2f553-201">Keep movement after object is released</span></span>

<span data-ttu-id="2f553-202">Per l'oggetto **TheModule**, aggiungi un componente **Rigidbody** per abilitare gli effetti della fisica e quindi deseleziona la casella di controllo **Use Gravity** (Usa la gravità) in modo che sull'oggetto non influisca la forza di gravità:</span><span class="sxs-lookup"><span data-stu-id="2f553-202">For the **TheModule** object, add a **Rigidbody** component to enable physics, and then un-check the **Use Gravity** checkbox so the object is not affected by gravity:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

<span data-ttu-id="2f553-204">Tornando al componente Manipulation Handler (Script) (Gestore manipolazione - Script), verifica che l'opzione **Release Behavior** (Comportamento al rilascio) sia impostata sia su **Keep Velocity** (Mantieni la velocità) che su **Keep Angular Velocity** (Mantieni la velocità angolare) in modo che, dopo essere stato rilasciato dalla mano dell'utente, l'oggetto continui a muoversi:</span><span class="sxs-lookup"><span data-stu-id="2f553-204">Back on the Manipulation Handler (Script) component, verify that the **Release Behavior** is set to both **Keep Velocity** and **Keep Angular Velocity** so that once the object is released from the user's hand, it continues to move:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

<span data-ttu-id="2f553-206">Per altre informazioni sul componente Manipulation Handler (Gestore manipolazione) e sulle relative proprietà associate, puoi visitare la guida su [tale gestore](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="2f553-206">To learn more about the Manipulation handler component and its associated properties, you can visit the [Manipulation handler](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="2f553-207">Aggiunta di cubi di delimitazione</span><span class="sxs-lookup"><span data-stu-id="2f553-207">Adding bounding boxes</span></span>

<span data-ttu-id="2f553-208">I cubi di delimitazione consentono di manipolare gli oggetti con una mano in modo più semplice e intuitivo per l'interazione sia da vicino che da lontano, in quanto forniscono punti di manipolazione utilizzabili per il ridimensionamento e la rotazione.</span><span class="sxs-lookup"><span data-stu-id="2f553-208">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="2f553-209">In questo esempio aggiungerai un cubo di delimitazione all'oggetto EarthCore in modo che ora sia possibile interagire con tale oggetto usando la manipolazione configurata nella sezione precedente, nonché ridimensionarlo e ruotarlo usando i punti di manipolazione del cubo di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="2f553-209">In this example, you will add a bounding box to the EarthCore object so this object can now be interacted with using the object manipulation you configured in the previous section, as well as, scaled and rotated using the bounding box handles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2f553-210">Per poter usare un **cubo di delimitazione**, è necessario che l'oggetto abbia i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="2f553-210">To be able to use a **bounding box**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="2f553-211">Componente **Collider** (Collisore), ad esempio un collisore cuboide</span><span class="sxs-lookup"><span data-stu-id="2f553-211">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="2f553-212">Componente **Bounding Box (Script)** (Cubo di delimitazione- Script)</span><span class="sxs-lookup"><span data-stu-id="2f553-212">**Bounding Box (Script)** component</span></span>

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a><span data-ttu-id="2f553-213">1. Aggiungere il componente Bounding Box (Script) (Cubo di delimitazione- Script) all'oggetto EarthCore</span><span class="sxs-lookup"><span data-stu-id="2f553-213">1. Add the Bounding Box (Script) component to the EarthCore object</span></span>

<span data-ttu-id="2f553-214">Nella finestra Inspector (Controllo) seleziona l'oggetto **EarthCore** e aggiungigli il componente **Bounding Box (Script)** (Cubo di delimitazione- Script):</span><span class="sxs-lookup"><span data-stu-id="2f553-214">In the Inspector window, select the **EarthCore** object and add the **Bounding Box (Script)** component to the EarthCore object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> <span data-ttu-id="2f553-216">Le visualizzazioni del cubo di delimitazione vengono create in fase di runtime, pertanto non sono visibili prima di passare alla modalità di gioco.</span><span class="sxs-lookup"><span data-stu-id="2f553-216">The Bounding Box visualizations is created at run time and therefore not visible before you enter Game mode.</span></span>

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a><span data-ttu-id="2f553-217">2. Visualizzare e provare il cubo di delimitazione usando la simulazione nell'editor</span><span class="sxs-lookup"><span data-stu-id="2f553-217">2. Visualize and test the bounding box using the in-editor simulation</span></span>

<span data-ttu-id="2f553-218">Fai clic sul pulsante Play (Esegui) per passare alla modalità di gioco.</span><span class="sxs-lookup"><span data-stu-id="2f553-218">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="2f553-219">Quindi tieni premuta la barra spaziatrice per visualizzare la mano e usare il mouse per interagire con il cubo di delimitazione:</span><span class="sxs-lookup"><span data-stu-id="2f553-219">Then press and hold the spacebar to bring up the hand and use the mouse to interact with the bounding box:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

<span data-ttu-id="2f553-221">Per altre informazioni sul componente Bounding Box (Cubo di delimitazione) e sulle relative proprietà associate, puoi visitare la guida su [tale componente](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="2f553-221">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-touch-effects"></a><span data-ttu-id="2f553-222">Aggiunta di effetti di tocco</span><span class="sxs-lookup"><span data-stu-id="2f553-222">Adding touch effects</span></span>

<span data-ttu-id="2f553-223">In questo esempio abiliterai l'attivazione di eventi al tocco di un oggetto con la mano.</span><span class="sxs-lookup"><span data-stu-id="2f553-223">In this example, you will enable events to be triggered when you touch an object with your hand.</span></span> <span data-ttu-id="2f553-224">Più specificamente, configurerai l'oggetto Octa in modo che riproduca un effetto sonoro quando l'utente lo tocca.</span><span class="sxs-lookup"><span data-stu-id="2f553-224">Specifically, you will configure the Octa object to play a sound effect when the user touches it.</span></span>

<span data-ttu-id="2f553-225">Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:</span><span class="sxs-lookup"><span data-stu-id="2f553-225">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="2f553-226">Aggiungere un componente Audio Source (Origine audio) all'oggetto</span><span class="sxs-lookup"><span data-stu-id="2f553-226">Add an Audio Source component to the object</span></span>
2. <span data-ttu-id="2f553-227">Aggiungere il componente Near Interaction Touchable (Script) (Toccabile con interazione da vicino - Script) all'oggetto</span><span class="sxs-lookup"><span data-stu-id="2f553-227">Add the Near Interaction Touchable (Script) component to the object</span></span>
3. <span data-ttu-id="2f553-228">Aggiungere il componente Hand Interaction Touch (Script) (Tocco con interazione manuale - Script) all'oggetto</span><span class="sxs-lookup"><span data-stu-id="2f553-228">Add the Hand Interaction Touch (Script) component to the object</span></span>
4. <span data-ttu-id="2f553-229">Implementare l'evento On Touch Started (Avviato al tocco)</span><span class="sxs-lookup"><span data-stu-id="2f553-229">Implement the On Touch Started event</span></span>
5. <span data-ttu-id="2f553-230">Provare l'interazione con tocco tramite la simulazione nell'editor</span><span class="sxs-lookup"><span data-stu-id="2f553-230">Test the touch interaction using the in-editor simulation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2f553-231">Per poter **attivare gli eventi di tocco**, è necessario che l'oggetto abbia i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="2f553-231">To be able to **trigger touch events**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="2f553-232">Componente **Collider** (Collisore), preferibilmente un collisore cuboide</span><span class="sxs-lookup"><span data-stu-id="2f553-232">**Collider** component, preferably a Box Collider</span></span>
> * <span data-ttu-id="2f553-233">Componente **Near Interaction Touchable (Script)** (Toccabile con interazione da vicino - Script)</span><span class="sxs-lookup"><span data-stu-id="2f553-233">**Near Interaction Touchable (Script)** component</span></span>
> * <span data-ttu-id="2f553-234">Componente **Hand Interaction Touch (Script)** (Tocco con interazione manuale - Script)</span><span class="sxs-lookup"><span data-stu-id="2f553-234">**Hand Interaction Touch (Script)** component</span></span>

> [!NOTE]
> <span data-ttu-id="2f553-235">Il componente Hand Interaction Touch (Script) (Tocco con interazione manuale - Script) non fa parte di MRTK.</span><span class="sxs-lookup"><span data-stu-id="2f553-235">The Hand Interaction Touch (Script) component is not part of MRTK.</span></span> <span data-ttu-id="2f553-236">È stato importato con gli asset di questa esercitazione e originariamente era incluso negli esempi Unity di Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="2f553-236">It was imported with this tutorial's assets and originally part of the MixedReality Toolkit Unity Examples.</span></span>

### <a name="1-add-an-audio-source-component-to-the-object"></a><span data-ttu-id="2f553-237">1. Aggiungere un componente Audio Source (Origine audio) all'oggetto</span><span class="sxs-lookup"><span data-stu-id="2f553-237">1. Add an Audio Source component to the object</span></span>

<span data-ttu-id="2f553-238">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Octa**, aggiungigli un componente **Audio Source** (Origine audio) e quindi imposta **Spatial Blend** (Blend spaziale) su 1 per abilitare l'audio spaziale:</span><span class="sxs-lookup"><span data-stu-id="2f553-238">In the Hierarchy window, select the **Octa** object, add an **Audio Source** component to the Octa object, and then change **Spatial Blend** to 1 to enable spatial audio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a><span data-ttu-id="2f553-240">2. Aggiungere il componente Near Interaction Touchable (Script) (Toccabile con interazione da vicino - Script) all'oggetto</span><span class="sxs-lookup"><span data-stu-id="2f553-240">2. Add the Near Interaction Touchable (Script) component to the object</span></span>

<span data-ttu-id="2f553-241">Con l'oggetto **Octa** ancora selezionato, aggiungigli il componente **Near Interaction Touchable (Script)** (Toccabile con interazione da vicino - Script) e quindi fai clic sui pulsanti **Fix Bounds** (Correggi limiti) e **Fix Center** (Correggi centro) per aggiornare le proprietà relative ai limiti e al centro in locale di tale componente in modo che corrispondano a BoxCollider:</span><span class="sxs-lookup"><span data-stu-id="2f553-241">With the **Octa** object still selected, add the **Near Interaction Touchable (Script)** component to the Octa object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a><span data-ttu-id="2f553-243">3. Aggiungere il componente Hand Interaction Touch (Script) (Tocco con interazione manuale - Script) all'oggetto</span><span class="sxs-lookup"><span data-stu-id="2f553-243">3. Add the Hand Interaction Touch (Script) component to the object</span></span>

<span data-ttu-id="2f553-244">Con l'oggetto **Octa** ancora selezionato, aggiungigli il componente **Hand Interaction Touch (Script)** (Tocco con interazione manuale - Script):</span><span class="sxs-lookup"><span data-stu-id="2f553-244">With the **Octa** object still selected, add the **Hand Interaction Touch (Script)** component to the Octa object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a><span data-ttu-id="2f553-246">4. Implementare l'evento On Touch Started (Avviato al tocco)</span><span class="sxs-lookup"><span data-stu-id="2f553-246">4. Implement the On Touch Started event</span></span>

<span data-ttu-id="2f553-247">Nel componente **Hand Interaction Touch (Script)** (Tocco con interazione manuale - Script) fai clic sulla piccola icona **+** per creare un nuovo evento **On Touch Started ()** (Avviato al tocco).</span><span class="sxs-lookup"><span data-stu-id="2f553-247">On the **Hand Interaction Touch (Script)** component, click the small **+** icon to create a new **On Touch Started ()** event.</span></span> <span data-ttu-id="2f553-248">Quindi configura l'oggetto **Octa** per ricevere l'evento e definisci **AudioSource.PlayOneShot** come azione da attivare:</span><span class="sxs-lookup"><span data-stu-id="2f553-248">Then configure the **Octa** object to receive the event and define **AudioSource.PlayOneShot** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

<span data-ttu-id="2f553-250">Passa ad **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Audio** per visualizzare i clip audio forniti con MRTK e quindi assegna un clip audio appropriato al campo **Audio Clip** (Clip audio), ad esempio MRTK_Gem:</span><span class="sxs-lookup"><span data-stu-id="2f553-250">Navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Audio** to see audio clips provided with the MRTK, and then assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> <span data-ttu-id="2f553-252">Per rivedere la procedura di implementazione degli eventi, puoi fare riferimento alle istruzioni contenute in [Movimenti di rilevamento della mano e pulsanti con supporto per interazioni](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).</span><span class="sxs-lookup"><span data-stu-id="2f553-252">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a><span data-ttu-id="2f553-253">5. Provare l'interazione con tocco tramite la simulazione nell'editor</span><span class="sxs-lookup"><span data-stu-id="2f553-253">5. Test the touch interaction using the in-editor simulation</span></span>

<span data-ttu-id="2f553-254">Fai clic sul pulsante Play (Esegui) per passare alla modalità di gioco.</span><span class="sxs-lookup"><span data-stu-id="2f553-254">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="2f553-255">Quindi tieni premuta la barra spaziatrice per visualizzare la mano e usare il mouse per toccare l'oggetto Octa e attivare l'effetto sonoro:</span><span class="sxs-lookup"><span data-stu-id="2f553-255">Then press and hold the spacebar to bring up the hand and use the mouse to touch the Octa object and trigger the sound effect:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> <span data-ttu-id="2f553-257">Come hai potuto notare quando hai provato l'interazione con tocco e come illustrato nell'immagine precedente, il colore dell'oggetto Octa si è messo a pulsare mentre l'oggetto veniva toccato.</span><span class="sxs-lookup"><span data-stu-id="2f553-257">As you saw when testing the touch interaction, and as shown in the image above, the Octa object color pulsated while it was touched.</span></span> <span data-ttu-id="2f553-258">Questo effetto è hardcoded nel componente Hand Interaction Touch (Script) (Tocco con interazione manuale - Script) e non deriva dalla configurazione dell'evento completata nella procedura sopra descritta.</span><span class="sxs-lookup"><span data-stu-id="2f553-258">This effect is hard coded into the Hand Interaction Touch (Script) component and not a result of the event configuration you completed in the steps above.</span></span>
>
> <span data-ttu-id="2f553-259">Se vuoi disabilitare questo effetto, puoi ad esempio impostare come commento la riga 32 'TargetRenderer = GetComponentInChildren<Renderer>();' in modo che TargetRenderer rimanga null e il colore non pulsi.</span><span class="sxs-lookup"><span data-stu-id="2f553-259">If you want to disable this effect, you can, for example, comment out or line 32 'TargetRenderer = GetComponentInChildren<Renderer>();' which will result in the TargetRenderer remaining null and the color not pulsating.</span></span>

## <a name="congratulations"></a><span data-ttu-id="2f553-260">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="2f553-260">Congratulations</span></span>

<span data-ttu-id="2f553-261">In questa esercitazione hai appreso come organizzare gli oggetti 3D in una raccolta sotto forma di griglia e come manipolare tali oggetti (ridimensionamento, rotazione e spostamento) usando l'interazione da vicino (afferrando direttamente con le mani tracciate) e l'interazione da lontano (tramite i raggi dello sguardo o i raggi della mano).</span><span class="sxs-lookup"><span data-stu-id="2f553-261">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate these objects (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="2f553-262">Hai anche appreso come delimitare gli oggetti 3D con cubi di delimitazione e come usare e personalizzare i punti di manipolazione presenti sui cubi di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="2f553-262">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the handles on the bounding boxes.</span></span> <span data-ttu-id="2f553-263">Hai infine appreso come attivare eventi nel momento in cui viene toccato un oggetto.</span><span class="sxs-lookup"><span data-stu-id="2f553-263">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="2f553-264">Lezione successiva: 6. Esplorazione delle opzioni di input avanzate</span><span class="sxs-lookup"><span data-stu-id="2f553-264">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)

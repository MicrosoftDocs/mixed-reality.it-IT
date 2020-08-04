---
title: Esercitazioni introduttive - 4 Posizionamento degli oggetti nella scena
description: Questo corso illustra come usare Mixed Reality Toolkit (MRTK) per creare un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 71990db23b5154de916f0eda86a978885ab53547
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376633"
---
# <a name="4-positioning-objects-in-the-scene"></a><span data-ttu-id="2d485-105">4. Posizionamento degli oggetti nella scena</span><span class="sxs-lookup"><span data-stu-id="2d485-105">4. Positioning objects in the scene</span></span>

## <a name="overview"></a><span data-ttu-id="2d485-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="2d485-106">Overview</span></span>

<span data-ttu-id="2d485-107">In questa esercitazione si importeranno gli asset dell'esercitazione e gli oggetti disponibili verranno posizionati nella scena.</span><span class="sxs-lookup"><span data-stu-id="2d485-107">In this tutorial, you will import the tutorial assets and position the provided objects in the scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="2d485-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="2d485-108">Objectives</span></span>

* <span data-ttu-id="2d485-109">Imparare a posizionare gli oggetti nella scena</span><span class="sxs-lookup"><span data-stu-id="2d485-109">Learn how to position objects in the scene</span></span>
* <span data-ttu-id="2d485-110">Imparare a usare la funzionalità Grid Object Collection (Raccolta di oggetti griglia) di MRTK</span><span class="sxs-lookup"><span data-stu-id="2d485-110">Learn how to use MRTK's Grid Object Collection feature</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="2d485-111">Importazione degli asset dell'esercitazione</span><span class="sxs-lookup"><span data-stu-id="2d485-111">Importing the tutorial assets</span></span>

<span data-ttu-id="2d485-112">Scaricare e importare il seguente pacchetto personalizzato di Unity:</span><span class="sxs-lookup"><span data-stu-id="2d485-112">Download and import the following Unity custom package:</span></span>

* [<span data-ttu-id="2d485-113">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="2d485-113">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)

<span data-ttu-id="2d485-114">Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="2d485-114">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="2d485-116">Per rivedere la procedura di importazione di un pacchetto personalizzato di Unity, fare riferimento alle istruzioni contenute in [Importazione di MRTK](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="2d485-116">For a reminder on how to import a Unity custom package, you can refer to the [Importing the MRTK](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="creating-the-parent-object"></a><span data-ttu-id="2d485-117">Creazione dell'oggetto padre</span><span class="sxs-lookup"><span data-stu-id="2d485-117">Creating the parent object</span></span>

<span data-ttu-id="2d485-118">Nella finestra Hierarchy (Gerarchia) fare clic con il pulsante destro del mouse su un'area vuota e scegliere **Create Empty** (Crea vuoto) per aggiungere un oggetto vuoto alla scena:</span><span class="sxs-lookup"><span data-stu-id="2d485-118">In the Hierarchy window, right-click on an empty spot, and select **Create Empty** to add an empty object to your scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="2d485-120">Per visualizzare le finestre della scena e di gioco affiancate, come mostrato nell'immagine precedente, trascinare la finestra di gioco a destra della finestra della scena.</span><span class="sxs-lookup"><span data-stu-id="2d485-120">To display your Scene and Game window side by side as shown in the image above, drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="2d485-121">Per altre informazioni sulla personalizzazione dell'area di lavoro, consultare l'argomento relativo alla <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">personalizzazione dell'area di lavoro</a> nella documentazione di Unity.</span><span class="sxs-lookup"><span data-stu-id="2d485-121">To learn more about customizing your workspace, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

<span data-ttu-id="2d485-122">Fare clic con il pulsante destro del mouse sull'oggetto appena creato, scegliere **Rename** (Rinomina) e modificare il nome in **RoverExplorer**:</span><span class="sxs-lookup"><span data-stu-id="2d485-122">Right-click on the newly created object, select **Rename**, and change the name to **RoverExplorer**:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-2.png)

<span data-ttu-id="2d485-124">Con l'oggetto RoverExplorer ancora selezionato, nella finestra Inspector (Controllo) configurare il componente **Transform** (Trasformazione) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="2d485-124">With the RoverExplorer object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="2d485-125">**Position** (Posizione): X = 0, Y = -0.6, Z = 2</span><span class="sxs-lookup"><span data-stu-id="2d485-125">**Position**: X = 0, Y = -0.6, Z = 2</span></span>
* <span data-ttu-id="2d485-126">**Rotation** (Rotazione): X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="2d485-126">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="2d485-127">**Scale** (Scala): X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="2d485-127">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="2d485-129">La fotocamera rappresenta la testa dell'utente ed è posizionata in corrispondenza dell'origine, X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="2d485-129">The camera represents the users head and is positioned at origin, X = 0, Y = 0, Z = 0.</span></span> <span data-ttu-id="2d485-130">In generale, 1 unità in Unity corrisponde a circa 1 metro nel mondo fisico.</span><span class="sxs-lookup"><span data-stu-id="2d485-130">In general, 1 unit in Unity is roughly 1 meter in the physical world.</span></span> <span data-ttu-id="2d485-131">Vi sono tuttavia eccezioni, ad esempio quando gli oggetti sono figli di oggetti ridimensionati.</span><span class="sxs-lookup"><span data-stu-id="2d485-131">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span> <span data-ttu-id="2d485-132">Nello scenario precedente, RoverExplorer è posizionato 2 metri in avanti e 0,6 metri in basso rispetto alla testa dell'utente.</span><span class="sxs-lookup"><span data-stu-id="2d485-132">In the scenario above, the RoverExplorer is positioned 2 meters in front of and 0.6 meters below the user's head.</span></span>

## <a name="adding-the-tutorial-prefabs"></a><span data-ttu-id="2d485-133">Aggiunta dei prefab per l'esercitazione</span><span class="sxs-lookup"><span data-stu-id="2d485-133">Adding the tutorial prefabs</span></span>

<span data-ttu-id="2d485-134">Nella finestra Project (Progetto) passare alla cartella **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** (Prefab):</span><span class="sxs-lookup"><span data-stu-id="2d485-134">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="2d485-136">Un <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> è un GameObject preconfigurato che viene archiviato come asset Unity e può essere riutilizzato nel progetto.</span><span class="sxs-lookup"><span data-stu-id="2d485-136">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="2d485-137">Dalla finestra Project (Progetto) fare clic e trascinare il prefab **Table** sull'oggetto **RoverExplorer** per renderlo figlio dell'oggetto RoverExplorer, quindi nella finestra Inspector (Controllo) configurare il componente **Transform** (Trasformazione) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="2d485-137">From the Project window, click-and-drag the **Table** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="2d485-138">**Position** (Posizione): X = 0, Y = -0.005, Z = 0</span><span class="sxs-lookup"><span data-stu-id="2d485-138">**Position**: X = 0, Y = -0.005, Z = 0</span></span>
* <span data-ttu-id="2d485-139">**Rotation** (Rotazione): X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="2d485-139">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="2d485-140">**Scale** (Scala): X = 1.2, Y = 0.01, Z = 1.2</span><span class="sxs-lookup"><span data-stu-id="2d485-140">**Scale**: X = 1.2, Y = 0.01, Z = 1.2</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="2d485-142">Per visualizzare la scena come illustrato nell'immagine seguente, usare <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a> (Gizmo della scena), nell'angolo in alto a destra della finestra della scena, per regolare l'angolo di visualizzazione in modo che si trovi sulll'asse Z in avanti, fare doppio clic sull'oggetto MixedRealityPlayspace per posizionare lo stato attivo sulla fotocamera ed eseguire lo zoom avanti necessario.</span><span class="sxs-lookup"><span data-stu-id="2d485-142">To display your scene as shown in the image above, use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis, double-click the MixedRealityPlayspace object to focus on the camera, and zoom in as needed.</span></span>

<span data-ttu-id="2d485-143">Dalla finestra Project (Progetto) fare clic e trascinare il prefab **RoverAssembly** sull'oggetto **RoverExplorer** per renderlo figlio dell'oggetto RoverExplorer, quindi nella finestra Inspector (Controllo) configurare il componente **Transform** (Trasformazione) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="2d485-143">From the Project window, click-and-drag the **RoverAssembly** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="2d485-144">**Position** (Posizione): X = -0.1, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="2d485-144">**Position**: X = -0.1, Y = 0, Z = 0</span></span>
* <span data-ttu-id="2d485-145">**Rotation** (Rotazione): X = 0, Y = -135, Z = 0</span><span class="sxs-lookup"><span data-stu-id="2d485-145">**Rotation**: X = 0, Y = -135, Z = 0</span></span>
* <span data-ttu-id="2d485-146">**Scale** (Scala): X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="2d485-146">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a><span data-ttu-id="2d485-148">Organizzazione di oggetti in una raccolta</span><span class="sxs-lookup"><span data-stu-id="2d485-148">Organizing objects in a collection</span></span>

<span data-ttu-id="2d485-149">Nella finestra Hierarchy (Gerarchia) fare clic con il pulsante destro del mouse sull'oggetto **RoverExplorer** e scegliere **Create Empty** (Crea vuoto) per aggiungere un oggetto vuoto come figlio di RoverExplorer, quindi assegnare all'oggetto il nome **RoverParts** e configurare il componente **Transform** (Trasformazione) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="2d485-149">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **RoverParts**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="2d485-150">**Position** (Posizione): X = 0, Y = 0.06, Z = 0</span><span class="sxs-lookup"><span data-stu-id="2d485-150">**Position**: X = 0, Y = 0.06, Z = 0</span></span>
* <span data-ttu-id="2d485-151">**Rotation** (Rotazione): X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="2d485-151">**Rotation**: X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="2d485-152">**Scale** (Scala): X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="2d485-152">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-1.png)

<span data-ttu-id="2d485-154">Nella finestra Hierarchy (Gerarchia) selezionare tutti gli oggetti figlio RoverExplorer > RoverAssembly > RoverModel > **Parts**, fare clic con il pulsante destro del mouse su di essi e scegliere **Duplicate** (Duplica) per creare una copia di ognuna delle parti:</span><span class="sxs-lookup"><span data-stu-id="2d485-154">In the Hierarchy window, select all the RoverExplorer > RoverAssembly > RoverModel > **Parts** child objects, right-click on them and select **Duplicate** to create a copy of each of the parts:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="2d485-156">Per selezionare più oggetti adiacenti, selezionare il primo e l'ultimo oggetto con il mouse tenendo premuto MAIUSC.</span><span class="sxs-lookup"><span data-stu-id="2d485-156">To select multiple adjacent objects, press-and-hold the SHIFT key while using the mouse to select the first and last object.</span></span>

<span data-ttu-id="2d485-157">Con gli oggetti figlio Parts appena duplicati ancora selezionati, fare clic e trascinarli sull'oggetto **RoverParts** per renderli oggetti figlio dell'oggetto RoverParts:</span><span class="sxs-lookup"><span data-stu-id="2d485-157">With the newly duplicated Parts child objects still selected, click-and-drag them on to the **RoverParts** object to make them child objects of the RoverParts object:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-3.png)

<span data-ttu-id="2d485-159">Per rendere più agevole l'uso della scena, nella finestra Hierarchy (Gerarchia) fare clic sull'icona a forma di **occhio** sulla sinistra dell'oggetto per disattivare la **visibilità nella scena** per l'oggetto **RoverExplorer**.</span><span class="sxs-lookup"><span data-stu-id="2d485-159">To make it easier to work with your scene, in the Hierarchy window, click the **eye** icon to the left of the object to toggle the **scene visibility** for the **RoverExplorer** object off.</span></span> <span data-ttu-id="2d485-160">In questo modo, l'oggetto viene nascosto nella finestra Scene (Scena) senza effetti sulla sua visibilità nel gioco:</span><span class="sxs-lookup"><span data-stu-id="2d485-160">This hides the object in the Scene window without changing its in-game visibility:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-4.png)

> [!TIP]
> <span data-ttu-id="2d485-162">Per altre informazioni sui controlli per la visibilità nella scena e su come usarli per ottimizzare la vista e il flusso di lavoro della scena, consultare l'argomento sulla <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">visibilità nella scena</a> nella documentazione di Unity.</span><span class="sxs-lookup"><span data-stu-id="2d485-162">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

<span data-ttu-id="2d485-163">Nella finestra Hierarchy (Gerarchia), ripulire i nomi degli oggetti figlio RoverParts sostituendo la parte finale **(1)** con **_Part**:</span><span class="sxs-lookup"><span data-stu-id="2d485-163">In the Hierarchy window, clean up the RoverParts child objects' names by replacing the appended **(1)** with **_Part**:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-5.png)

<span data-ttu-id="2d485-165">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **RoverParts**, quindi nella finestra Inspector (Controllo) fare clic sul pulsante **Add Component** (Aggiungi componente) e cercare e selezionare **GridObjectCollection** per aggiungere il componente GridObjectCollection all'oggetto RoverParts:</span><span class="sxs-lookup"><span data-stu-id="2d485-165">In the Hierarchy window, select the **RoverParts** object, then in the Inspector window, click the **Add Component** button, and search for and select **GridObjectCollection** to add the GridObjectCollection component to the RoverParts object:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-6.png)

<span data-ttu-id="2d485-167">Configurare i valori del componente **GridObjectCollection** come segue:</span><span class="sxs-lookup"><span data-stu-id="2d485-167">Configure the **GridObjectCollection** component values as follows:</span></span>

* <span data-ttu-id="2d485-168">**Sort Type** (Tipo di ordinamento): Alfabetico</span><span class="sxs-lookup"><span data-stu-id="2d485-168">**Sort Type**: Alphabetic</span></span>
* <span data-ttu-id="2d485-169">**Layout**: Orizzontale</span><span class="sxs-lookup"><span data-stu-id="2d485-169">**Layout**: Horizontal</span></span>
* <span data-ttu-id="2d485-170">**Cell Width** (Larghezza cella): 0,25</span><span class="sxs-lookup"><span data-stu-id="2d485-170">**Cell Width**: 0.25</span></span>
* <span data-ttu-id="2d485-171">**Distance from parent** (Distanza dal padre): 0,38</span><span class="sxs-lookup"><span data-stu-id="2d485-171">**Distance from parent**: 0.38</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-7.png)

<span data-ttu-id="2d485-173">Fare quindi clic sul pulsante **Update Collection** (Aggiorna raccolta) per aggiornare la posizione degli oggetti figlio RoverParts:</span><span class="sxs-lookup"><span data-stu-id="2d485-173">Then click the **Update Collection** button to update the position of the RoverParts child objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="2d485-175">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="2d485-175">Congratulations</span></span>

<span data-ttu-id="2d485-176">In questa esercitazione è stato illustrato come posizionare gli oggetti nella scena in relazione all'utente e come usare la funzionalità Grid Object Collection (Raccolta di oggetti griglia) di MRTK per organizzare gli oggetti in una raccolta.</span><span class="sxs-lookup"><span data-stu-id="2d485-176">In this tutorial, you learned how to position objects in the scene relative to the user and use MRTK's Grid Object Collection feature to organize objects in a collection.</span></span>

[<span data-ttu-id="2d485-177">Esercitazione successiva: 5. Creazione di contenuto dinamico tramite risolutori</span><span class="sxs-lookup"><span data-stu-id="2d485-177">Next Tutorial: 5. Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)

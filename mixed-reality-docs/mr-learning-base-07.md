---
title: Esercitazioni introduttive - 7 Interazione con oggetti 3D
description: Questo corso illustra come usare Mixed Reality Toolkit (MRTK) per creare un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 8920b35d1583777b86bc82868bb90338e25298e2
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304971"
---
# <a name="7-interacting-with-3d-objects"></a><span data-ttu-id="5b139-105">7. Interazione con oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="5b139-105">7. Interacting with 3D objects</span></span>

<span data-ttu-id="5b139-106">In questa esercitazione apprenderai come abilitare la manipolazione da vicino e da lontano degli oggetti 3D e limitare i tipi di manipolazione consentiti.</span><span class="sxs-lookup"><span data-stu-id="5b139-106">In this tutorial, you will learn how to enable near and far manipulation of 3D objects and limit the allowed types of manipulation.</span></span> <span data-ttu-id="5b139-107">Apprenderai anche come aggiungere cubi di delimitazione intorno agli oggetti 3D per controllare più facilmente la manipolazione degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="5b139-107">You will also learn how to add bounding boxes around 3D objects to make it easier to control the object manipulation.</span></span>

## <a name="objectives"></a><span data-ttu-id="5b139-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="5b139-108">Objectives</span></span>

* <span data-ttu-id="5b139-109">Apprendere come configurare gli oggetti 3D in modo che sia possibile interagire con essi</span><span class="sxs-lookup"><span data-stu-id="5b139-109">Learn how to configure 3D objects so they can be interacted with</span></span>
* <span data-ttu-id="5b139-110">Apprendere come aggiungere cubi di delimitazione a oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="5b139-110">Learn how to add bounding boxes to 3D objects</span></span>

## <a name="manipulating-3d-objects"></a><span data-ttu-id="5b139-111">Manipolazione di oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="5b139-111">Manipulating 3D objects</span></span>

<span data-ttu-id="5b139-112">In questa sezione aggiungerai la possibilità di manipolare tutte le parti rover organizzate sul tavolo durante l'esercitazione [Posizionamento degli oggetti nella scena](mr-learning-base-04.md).</span><span class="sxs-lookup"><span data-stu-id="5b139-112">In this section, you will add the ability to manipulate all the Rover parts you organized on the table during the [Positioning objects in the scene](mr-learning-base-04.md) tutorial.</span></span>

<span data-ttu-id="5b139-113">Di seguito sono elencati i passaggi principali da eseguire per ottenere questo risultato:</span><span class="sxs-lookup"><span data-stu-id="5b139-113">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="5b139-114">Aggiungere il componente Object Manipulator (Script) (Manipolatore oggetti - script) a tutti gli oggetti parte</span><span class="sxs-lookup"><span data-stu-id="5b139-114">Add the Object Manipulator (Script) component to all the part objects</span></span>
2. <span data-ttu-id="5b139-115">Aggiungere il componente NearInteractionGrabbable a tutti gli oggetti parte</span><span class="sxs-lookup"><span data-stu-id="5b139-115">Add the NearInteractionGrabbable component to all the part objects</span></span>
3. <span data-ttu-id="5b139-116">Configurare il componente Object Manipulator (Script) (Manipolatore oggetti - script)</span><span class="sxs-lookup"><span data-stu-id="5b139-116">Configure the Object Manipulator (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="5b139-117">Per poter **manipolare un oggetto**, è necessario che l'oggetto abbia i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="5b139-117">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="5b139-118">Componente **Collider** (Collisore), ad esempio un collisore cuboide</span><span class="sxs-lookup"><span data-stu-id="5b139-118">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="5b139-119">Componente **Object Manipulator (Script)** (Manipolatore oggetti - script)</span><span class="sxs-lookup"><span data-stu-id="5b139-119">**Object Manipulator (Script)** component</span></span>
>
> <span data-ttu-id="5b139-120">Per poter **manipolare** e **afferrare un oggetto con le mani tracciate**, è necessario che l'oggetto abbia i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="5b139-120">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="5b139-121">Componente **Collider** (Collisore), ad esempio un collisore cuboide</span><span class="sxs-lookup"><span data-stu-id="5b139-121">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="5b139-122">Componente **Object Manipulator (Script)** (Manipolatore oggetti - script)</span><span class="sxs-lookup"><span data-stu-id="5b139-122">**Object Manipulator (Script)** component</span></span>
> * <span data-ttu-id="5b139-123">Componente **NearInteractionGrabbable**</span><span class="sxs-lookup"><span data-stu-id="5b139-123">**NearInteractionGrabbable** component</span></span>

<span data-ttu-id="5b139-124">Configurerai inoltre Rover Explorer (Esplora rover) in modo che sia possibile posizionare le parti rover sul rover per renderlo un assembly di rover completo.</span><span class="sxs-lookup"><span data-stu-id="5b139-124">Additionally, you will configure the Rover Explorer so that you can place the rover parts on to the Rover to make it a complete rover assembly.</span></span>

<span data-ttu-id="5b139-125">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto RoverExplorer > **RoverParts** e seleziona tutti i relativi oggetti parte rover figlio e l'oggetto **RoverAssembly**, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere i componenti seguenti a tutti gli oggetti selezionati:</span><span class="sxs-lookup"><span data-stu-id="5b139-125">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects and the **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="5b139-126">Componente **Object Manipulator (Script)** (Manipolatore oggetti - script)</span><span class="sxs-lookup"><span data-stu-id="5b139-126">**Object Manipulator (Script)** component</span></span>
* <span data-ttu-id="5b139-127">Componente **NearInteractionGrabbable**</span><span class="sxs-lookup"><span data-stu-id="5b139-127">**NearInteractionGrabbable** component</span></span>
* <span data-ttu-id="5b139-128">Componente **Part Assembly Controller (Script)** (Controllo assembly parti - script)</span><span class="sxs-lookup"><span data-stu-id="5b139-128">**Part Assembly Controller (Script)** component</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="5b139-130">Per selezionare più oggetti non adiacenti, tieni premuto CTRL mentre usi il mouse per selezionare un oggetto.</span><span class="sxs-lookup"><span data-stu-id="5b139-130">To select multiple objects that are not next to each other, press-and-hold the CTRL key while using the mouse to select any object.</span></span>

> [!NOTE]
> <span data-ttu-id="5b139-131">Ai fini di questa esercitazione, i collisori sono già stati aggiunti alle parti rover.</span><span class="sxs-lookup"><span data-stu-id="5b139-131">For the purpose of this tutorial, colliders have already been added to the rover parts.</span></span> <span data-ttu-id="5b139-132">Per altre informazioni sui collisori, puoi visitare la documentazione <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">corrispondente</a> di Unity.</span><span class="sxs-lookup"><span data-stu-id="5b139-132">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="5b139-133">Part Assembly Controller (Script) (Controllo assembly parti - script) non fa parte di MRTK, ma è stato incluso negli asset dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="5b139-133">The Part Assembly Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="5b139-134">Con tutti gli oggetti parte rover e l'oggetto RoverAssembly ancora selezionati, nella finestra Inspector (Controllo) configura il componente **Object Manipulator (Script)** (Manipolatore oggetti - script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="5b139-134">With all the rover part objects and the RoverAssembly object still selected, in the Inspector window, configure the **Object Manipulator (Script)** component as follows:</span></span>

* <span data-ttu-id="5b139-135">Dall'elenco a discesa **Two Handed Manipulation Type** (Tipo di manipolazione a due mani) deseleziona Scale (Scala) in modo che siano abilitate solo le opzioni **Move** (Sposta) e **Rotate** (Ruota)</span><span class="sxs-lookup"><span data-stu-id="5b139-135">From the **Two Handed Manipulation Type** dropdown, uncheck the Scale, so only **Move** and **Rotate** is enabled</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> <span data-ttu-id="5b139-137">A questo punto hai abilitato la manipolazione per tutti gli oggetti parte rover e per l'oggetto RoverAssembly.</span><span class="sxs-lookup"><span data-stu-id="5b139-137">At this point, you have enabled object manipulation for all the rover part objects and the RoverAssembly object.</span></span>

<span data-ttu-id="5b139-138">Nella finestra Project (Progetto) passa alla cartella **Assets (Asset)**  > **MRTK** > **SDK** > **StandardAssets** > **Audio** per individuare i clip audio:</span><span class="sxs-lookup"><span data-stu-id="5b139-138">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Audio** folder to locate the audio clips:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-3.png)

<span data-ttu-id="5b139-140">Nella finestra Hierarchy (Gerarchia) seleziona di nuovo gli **oggetti parte rover** e quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Audio Sources** (Origini audio) e configuralo come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="5b139-140">In the Hierarchy window, reselect all the **rover part objects**, then in the Inspector window, use the **Add Component** button to add the **Audio Sources** component and configure it as follows:</span></span>

* <span data-ttu-id="5b139-141">Assegna il clip audio **MRTK_Scale_Start** al campo **AudioClip**</span><span class="sxs-lookup"><span data-stu-id="5b139-141">Assign the **MRTK_Scale_Start** audio clip to the **AudioClip** field</span></span>
* <span data-ttu-id="5b139-142">Deseleziona la casella di controllo **Play On Awake** (Riproduci quando operativo)</span><span class="sxs-lookup"><span data-stu-id="5b139-142">Uncheck the **Play On Awake** checkbox</span></span>
* <span data-ttu-id="5b139-143">Modifica il campo **Spatial Blend** (Blend spaziale) impostandolo su 1</span><span class="sxs-lookup"><span data-stu-id="5b139-143">Change **Spatial Blend** to 1</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-4.png)

<span data-ttu-id="5b139-145">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** in modo da rivelare tutti gli oggetti suggerimento di posizionamento, quindi scegli la prima parte rover, RoverParts > **Camera_Part**, e configura il componente **Part Assembly Controller (Script)** (Controllo assembly parti - script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="5b139-145">In the Hierarchy window, expand the RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** object to reveal all of the placement hint objects, then select the first rover part, RoverParts > **Camera_Part**, and configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="5b139-146">Assegna l'oggetto **Camera_PlacementHint** al campo **Location To Place** (Punto di posizionamento)</span><span class="sxs-lookup"><span data-stu-id="5b139-146">Assign the **Camera_PlacementHint** object to the **Location To Place** field</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-5.png)

<span data-ttu-id="5b139-148">**Ripeti** questo passaggio per ognuno degli oggetti parte rover rimanenti e per l'oggetto RoverAssembly per configurare il componente **Part Assembly Controller (Script)** (Controllo assembly parti - script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="5b139-148">**Repeat** this step for each of the remaining rover part objects and the RoverAssembly object to configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="5b139-149">Per **Generator_Part**, assegna l'oggetto **Generator_PlacementHint** al campo **Location To Place** (Punto di posizionamento)</span><span class="sxs-lookup"><span data-stu-id="5b139-149">For the **Generator_Part**, assign the **Generator_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="5b139-150">Per **Lights_Part**, assegna l'oggetto **Lights_PlacementHint** al campo **Location To Place** (Punto di posizionamento)</span><span class="sxs-lookup"><span data-stu-id="5b139-150">For the **Lights_Part**, assign the **Lights_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="5b139-151">Per **UHFAntenna_Part**, assegna l'oggetto **UHFAntenna_PlacementHint** al campo **Location To Place** (Punto di posizionamento)</span><span class="sxs-lookup"><span data-stu-id="5b139-151">For the **UHFAntenna_Part**, assign the **UHFAntenna_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="5b139-152">Per **Spectrometer_Part**, assegna l'oggetto **Spectrometer_PlacementHint** al campo **Location To Place** (Punto di posizionamento)</span><span class="sxs-lookup"><span data-stu-id="5b139-152">For the **Spectrometer_Part**, assign the **Spectrometer_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="5b139-153">Per **RoverAssembly**, assegna l'oggetto stesso., ovvero l'oggetto **RoverAssembly** stesso, al campo **Location To Place** (Punto di posizionamento)</span><span class="sxs-lookup"><span data-stu-id="5b139-153">For the **RoverAssembly**, assign the object itself, i.e. the same **RoverAssembly** object, to the **Location To Place** field</span></span>

<span data-ttu-id="5b139-154">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto pulsante RoverExplorer > Buttons (Pulsanti) > **Reset** (Reimposta) e quindi nella finestra Inspector (Controllo) configura l'evento **OnClick ()** con supporto per interazioni come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="5b139-154">In the Hierarchy window, select the RoverExplorer > Buttons > **Reset** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="5b139-155">Assegna l'oggetto **RoverAssembly** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="5b139-155">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="5b139-156">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **PartAssemblyController** > **ResetPlacement ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="5b139-156">From the **No Function** dropdown, select **PartAssemblyController** > **ResetPlacement ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-6.png)

<span data-ttu-id="5b139-158">Se attivi ora la modalità di gioco, puoi usare l'interazione da vicino o da lontano per posizionare le parti rover sul rover.</span><span class="sxs-lookup"><span data-stu-id="5b139-158">If you now enter Game mode, you can use near or far interaction to place the rover parts on to the Rover.</span></span> <span data-ttu-id="5b139-159">Quando è vicina al suggerimento di posizionamento corrispondente, la parte si blocca in posizione e diventa parte del rover.</span><span class="sxs-lookup"><span data-stu-id="5b139-159">Once the part is close to the corresponding placement hint, it will snap into place and become part of the Rover.</span></span> <span data-ttu-id="5b139-160">Per reimpostare i posizionamenti, puoi scegliere il pulsante Reset (Reimposta):</span><span class="sxs-lookup"><span data-stu-id="5b139-160">To reset the placements, you can press the Reset button:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-7.png)

<span data-ttu-id="5b139-162">Per altre informazioni sul componente Object Manipulator (Manipolatore oggetti) e sulle relative proprietà associate, puoi visitare la guida su [tale componente](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="5b139-162">To learn more about the Object Manipulator component and its associated properties, you can visit the [Object Manipulator](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="5b139-163">Aggiunta di cubi di delimitazione</span><span class="sxs-lookup"><span data-stu-id="5b139-163">Adding bounding boxes</span></span>

<span data-ttu-id="5b139-164">I cubi di delimitazione consentono di manipolare gli oggetti con una mano in modo più semplice e intuitivo per l'interazione sia da vicino che da lontano, in quanto forniscono punti di manipolazione utilizzabili per il ridimensionamento e la rotazione.</span><span class="sxs-lookup"><span data-stu-id="5b139-164">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="5b139-165">In questo esempio aggiungerai un cubo di delimitazione all'oggetto RoverExplorer in modo da poter spostare, ruotare e ridimensionare facilmente l'intera esperienza.</span><span class="sxs-lookup"><span data-stu-id="5b139-165">In this example, you will add a bounding box to the RoverExplorer object so the whole experience can easily be moved, rotated, and scaled.</span></span> <span data-ttu-id="5b139-166">Configurerai inoltre il menu in modo che sia possibile abilitare e disabilitare il cubo di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="5b139-166">Additionally, you will configure the Menu so you can turn the Bounding Box on and off.</span></span>

<span data-ttu-id="5b139-167">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **RoverExplorer**, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="5b139-167">In the Hierarchy window, select the **RoverExplorer** object, then in the Inspector window, use the **Add Component** button to add the following components:</span></span>

* <span data-ttu-id="5b139-168">Componente **BoundingBox**</span><span class="sxs-lookup"><span data-stu-id="5b139-168">**BoundingBox** component</span></span>
* <span data-ttu-id="5b139-169">Componente **Object Manipulator (Script)** (Manipolatore oggetti - script)</span><span class="sxs-lookup"><span data-stu-id="5b139-169">**Object Manipulator (Script)** component</span></span>

<span data-ttu-id="5b139-170">**Deseleziona** quindi la casella di controllo accanto a entrambi i componenti in modo che siano **disabilitati** per impostazione predefinita:</span><span class="sxs-lookup"><span data-stu-id="5b139-170">Then **uncheck** the checkbox next to both components to make them **disabled** by default:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="5b139-172">La visualizzazione del cubo di delimitazione viene creata in fase di runtime e pertanto non è visibile prima di passare alla modalità di gioco.</span><span class="sxs-lookup"><span data-stu-id="5b139-172">The Bounding Box visualization is created at runtime and, therefore, not visible before you enter Game mode.</span></span>

> [!NOTE]
> <span data-ttu-id="5b139-173">Il componente BoundingBox aggiungerà automaticamente il componente NearInteractionGrabbable in fase di runtime.</span><span class="sxs-lookup"><span data-stu-id="5b139-173">The BoundingBox component will automatically add the NearInteractionGrabbable component at runtime.</span></span> <span data-ttu-id="5b139-174">Non è necessario pertanto aggiungere questo componente per afferrare con le mani tracciate gli oggetti racchiusi.</span><span class="sxs-lookup"><span data-stu-id="5b139-174">Therefore, we do not need to add this component to grab the enclosed objects with tracked hands.</span></span>

<span data-ttu-id="5b139-175">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto Menu > **ButtonCollection** in modo da rivelare i quattro pulsanti e rinomina il terzo pulsante come **BoundingBox_Enable**, quindi nella finestra Inspector (Controllo) configura il componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="5b139-175">In the Hierarchy window, expand the Menu > **ButtonCollection** object to reveal the four buttons and rename the third button to **BoundingBox_Enable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="5b139-176">Imposta **Main Label Text** (Testo etichetta principale) su **Enable** (Abilita)</span><span class="sxs-lookup"><span data-stu-id="5b139-176">Change the **Main Label Text** to **Enable**</span></span>
* <span data-ttu-id="5b139-177">Assegna l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="5b139-177">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="5b139-178">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **BoundingBox** > **bool Enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="5b139-178">From the **No Function** dropdown, select **BoundingBox** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="5b139-179">Verifica che la casella di controllo dell'argomento sia **selezionata**</span><span class="sxs-lookup"><span data-stu-id="5b139-179">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="5b139-180">Fai clic sull'icona **+** piccola per aggiungere un altro evento</span><span class="sxs-lookup"><span data-stu-id="5b139-180">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="5b139-181">Assegna l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="5b139-181">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="5b139-182">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **ObjectManipulator** > **bool Enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="5b139-182">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="5b139-183">Verifica che la casella di controllo dell'argomento sia **selezionata**</span><span class="sxs-lookup"><span data-stu-id="5b139-183">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="5b139-184">Lascia per **Icon** (Icona) l'impostazione di icona 'cubo con cubo di delimitazione'</span><span class="sxs-lookup"><span data-stu-id="5b139-184">Leave the **Icon** as the 'cube with bounding box' icon</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-2.png)

<span data-ttu-id="5b139-186">Rinomina il quarto e ultimo pulsante come **BoundingBox_Disable**, quindi nella finestra Inspector (Controllo) configura il componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="5b139-186">Rename the forth and last button to **BoundingBox_Disable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="5b139-187">Imposta **Main Label Text** (Testo etichetta principale) su **Disable** (Disabilita)</span><span class="sxs-lookup"><span data-stu-id="5b139-187">Change the **Main Label Text** to **Disable**</span></span>
* <span data-ttu-id="5b139-188">Assegna l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="5b139-188">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="5b139-189">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **BoundingBox** > **bool Enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="5b139-189">From the **No Function** dropdown, select **BoundingBox** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="5b139-190">Verifica che la casella di controllo dell'argomento sia **deselezionata**</span><span class="sxs-lookup"><span data-stu-id="5b139-190">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="5b139-191">Fai clic sull'icona **+** piccola per aggiungere un altro evento</span><span class="sxs-lookup"><span data-stu-id="5b139-191">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="5b139-192">Assegna l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="5b139-192">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="5b139-193">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **ObjectManipulator** > **bool Enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="5b139-193">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="5b139-194">Verifica che la casella di controllo dell'argomento sia **deselezionata**</span><span class="sxs-lookup"><span data-stu-id="5b139-194">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="5b139-195">Modifica l'impostazione di **Icon** (Icona) configurando l'icona 'cubo con cubo di delimitazione'</span><span class="sxs-lookup"><span data-stu-id="5b139-195">Change the **Icon** to the 'cube with bounding box" icon</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-3.png)

<span data-ttu-id="5b139-197">Se ora attivi la modalità di gioco e abiliti il cubo di delimitazione facendo clic sul pulsante Enable (Abilita), puoi usare l'interazione da vicino o da lontano per spostare, ruotare e ridimensionare il cubo di delimitazione e usare il pulsante Disable (Disabilita) per disabilitare nuovamente il cubo di delimitazione:</span><span class="sxs-lookup"><span data-stu-id="5b139-197">If you now enter Game mode and enable the Bounding Box by clicking the Enable button, you can use near or far interaction to move, rotate, and scale the Bounding Box, and use the Disable button to disable the Bounding Box again:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-4.png)

<span data-ttu-id="5b139-199">Per altre informazioni sul componente Bounding Box (Cubo di delimitazione) e sulle relative proprietà associate, puoi visitare la guida su [tale componente](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="5b139-199">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="5b139-200">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="5b139-200">Congratulations</span></span>

<span data-ttu-id="5b139-201">In questa esercitazione hai appreso come abilitare la manipolazione da vicino e da lontano degli oggetti 3D e limitare i tipi di manipolazione consentiti.</span><span class="sxs-lookup"><span data-stu-id="5b139-201">In this tutorial, you learned how to enable near and far manipulation for 3D objects and how to limit the allowed types of manipulation.</span></span> <span data-ttu-id="5b139-202">Hai appreso anche come aggiungere cubi di delimitazione intorno agli oggetti 3D per controllare più facilmente la manipolazione degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="5b139-202">You also learned how to add bounding boxes around 3D objects to make it easier to control the object manipulation.</span></span>

[<span data-ttu-id="5b139-203">Esercitazione successiva: 8. Uso del tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="5b139-203">Next Tutorial: 8. Using eye-tracking</span></span>](mr-learning-base-08.md)

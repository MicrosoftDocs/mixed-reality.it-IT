---
title: Esercitazioni introduttive - 8 Uso del tracciamento oculare
description: Questo corso illustra come usare Mixed Reality Toolkit (MRTK) per creare un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 9a9fc7f860e6bf9c5cb3370a9c9ff11e627fe73f
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305674"
---
# <a name="8-using-eye-tracking"></a><span data-ttu-id="a1d13-105">8. Uso del tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="a1d13-105">8. Using eye-tracking</span></span>

## <a name="overview"></a><span data-ttu-id="a1d13-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="a1d13-106">Overview</span></span>

<span data-ttu-id="a1d13-107">In questa esercitazione si apprenderà come abilitare il tracciamento oculare per HoloLens 2 e aggiungere questa funzionalità agli oggetti, in modo da attivare le azioni quando l'utente rivolge loro lo sguardo.</span><span class="sxs-lookup"><span data-stu-id="a1d13-107">In this tutorial, you will learn how to enable eye-tracking for HoloLens 2 and add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!NOTE]
> <span data-ttu-id="a1d13-108">Se si distribuisce questo progetto anche in HoloLens (prima generazione), tenere presente che il tracciamento oculare è supportato solo in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a1d13-108">If you are also deploying this project to HoloLens (1st generation), note that eye-tracking is only supported on HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="a1d13-109">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="a1d13-109">Objectives</span></span>

* <span data-ttu-id="a1d13-110">Imparare ad abilitare il tracciamento oculare per HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a1d13-110">Learn how to enable eye-tracking for HoleLens 2</span></span>
* <span data-ttu-id="a1d13-111">Imparare a usare il tracciamento oculare per attivare un'azione</span><span class="sxs-lookup"><span data-stu-id="a1d13-111">Learn how to use eye-tracking to trigger action</span></span>

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="a1d13-112">Verifica dell'abilitazione della funzionalità di input mediante sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="a1d13-112">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="a1d13-113">Nel menu di Unity selezionare Mixed Reality Toolkit > Utilities > **Configure Unity Project** (Mixed Reality Toolkit > Utilità > Configura progetto Unity) per aprire la finestra **MRTK Project Configurator** (Configuratore del progetto MRTK) e quindi, nella sezione **UWP Capabilities** (Funzionalità UWP), verificare che l'opzione **Enable Eye Gaze Input Capability** (Abilita la funzionalità di input mediante sguardo fisso) sia disattivata:</span><span class="sxs-lookup"><span data-stu-id="a1d13-113">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="a1d13-115">La funzionalità di input mediante sguardo fisso dovrebbe essere stata abilitata durante la configurazione delle istruzioni riportate in [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) (Applicare le impostazioni del Configuratore del progetto MRTK) quando è stato configurato il progetto Unity all'inizio di questa serie di esercitazioni.</span><span class="sxs-lookup"><span data-stu-id="a1d13-115">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="a1d13-116">Se, tuttavia, non è abilitata, assicurarsi di farlo ora.</span><span class="sxs-lookup"><span data-stu-id="a1d13-116">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="a1d13-117">Abilitazione dello sguardo fisso nel provider di dati per lo sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="a1d13-117">Enabling eye based gaze in the gaze provider</span></span>

<span data-ttu-id="a1d13-118">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) selezionare la scheda MixedRealityToolkit > **Input** e seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="a1d13-118">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="a1d13-119">Clonare il profilo **DefaultHoloLens2InputSystemProfile** e assegnargli un nome appropriato, ad esempio _GettingStarted_HoloLens2InputSystemProfile_</span><span class="sxs-lookup"><span data-stu-id="a1d13-119">Clone the **DefaultHoloLens2InputSystemProfile** and give it a suitable name, for example, _GettingStarted_HoloLens2InputSystemProfile_</span></span>
* <span data-ttu-id="a1d13-120">Espandere la sezione**Pointers** (Puntatori)</span><span class="sxs-lookup"><span data-stu-id="a1d13-120">Expand the **Pointers** section</span></span>
* <span data-ttu-id="a1d13-121">Clonare il profilo **DefaultMixedRealityPointerProfile** e assegnargli un nome appropriato, ad esempio _GettingStarted_MixedRealityPointerProfile_</span><span class="sxs-lookup"><span data-stu-id="a1d13-121">Clone the **DefaultMixedRealityPointerProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityPointerProfile_</span></span>
* <span data-ttu-id="a1d13-122">Individuare la sezione **Gaze Settings** (Impostazioni sguardo) e selezionare la casella di controllo **Is Eye Tracking Enabled** (Tracciamento oculare abilitato)</span><span class="sxs-lookup"><span data-stu-id="a1d13-122">Locate the **Gaze Settings** section and check the **Is Eye Tracking Enabled** checkbox</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="a1d13-124">Per rivedere la procedura di clonazione dei profili di MRTK, fare riferimento alle istruzioni riportate in [Configurazione dei profili di Mixed Reality Toolkit](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="a1d13-124">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a><span data-ttu-id="a1d13-125">Abilitazione del tracciamento oculare simulato per l'editor di Unity</span><span class="sxs-lookup"><span data-stu-id="a1d13-125">Enabling simulated eye-tracking for the Unity editor</span></span>

<span data-ttu-id="a1d13-126">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit**, nella finestra Inspector (Controllo) passare alla scheda **Input** e quindi:</span><span class="sxs-lookup"><span data-stu-id="a1d13-126">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, navigate to the **Input** tab, then:</span></span>

* <span data-ttu-id="a1d13-127">Espandere la sezione **Input Data Providers** > **Input Simulation Service** (Provider di dati di input > Servizio di simulazione input)</span><span class="sxs-lookup"><span data-stu-id="a1d13-127">Expand the **Input Data Providers** > **Input Simulation Service** section</span></span>
* <span data-ttu-id="a1d13-128">Clonare il profilo **DefaultMixedRealityInputSimulationProfile** e assegnargli un nome appropriato, ad esempio _GettingStarted_MixedRealityInputSimulationProfile_</span><span class="sxs-lookup"><span data-stu-id="a1d13-128">Clone the **DefaultMixedRealityInputSimulationProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityInputSimulationProfile_</span></span>
* <span data-ttu-id="a1d13-129">Individuare la sezione **Eye Simulation** (Simulazione oculare) e selezionare la casella di controllo **Simulate Eye Position** (Simula posizione oculare)</span><span class="sxs-lookup"><span data-stu-id="a1d13-129">Locate the **Eye Simulation** section and check the **Simulate Eye Position** checkbox</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a><span data-ttu-id="a1d13-131">Aggiunta del tracciamento oculare agli oggetti</span><span class="sxs-lookup"><span data-stu-id="a1d13-131">Adding eye-tracking to objects</span></span>

<span data-ttu-id="a1d13-132">Nella finestra Hierarchy (Gerarchia) espandere l'oggetto RoverExplorer > **Buttons** (Pulsanti) e quindi, per ognuno dei tre oggetti pulsante figlio, espandere e selezionare l'oggetto SeeItSayItLabel > **TextMeshPro**:</span><span class="sxs-lookup"><span data-stu-id="a1d13-132">In the Hierarchy window, expand the RoverExplorer > **Buttons** object, then for each of the three child button objects, expand and select the SeeItSayItLabel > **TextMeshPro** object:</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-1.png)

<span data-ttu-id="a1d13-134">Con i tre oggetti TextMeshPro ancora selezionati, nella finestra Inspector (Controllo) usare il pulsante **Add Component** (Aggiungi componente) per aggiungere i componenti seguenti a tutti gli oggetti selezionati:</span><span class="sxs-lookup"><span data-stu-id="a1d13-134">With the three TextMeshPro objects still selected, in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="a1d13-135">Componente **Box Collider** (Collisore cubico)</span><span class="sxs-lookup"><span data-stu-id="a1d13-135">**Box Collider** component</span></span>
* <span data-ttu-id="a1d13-136">Componente **EyeTrackingTarget**</span><span class="sxs-lookup"><span data-stu-id="a1d13-136">**EyeTrackingTarget** component</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-2.png)

<span data-ttu-id="a1d13-138">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **Hints** (Suggerimenti) > SeeItSayItLabel > **TextMeshPro** e quindi configurare il componente **EyeTrackingTarget** come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="a1d13-138">In the Hierarchy window, select the **Hints** > SeeItSayItLabel > **TextMeshPro** object, then configure the **EyeTrackingTarget** component as follows:</span></span>

* <span data-ttu-id="a1d13-139">Nella sezione dell'evento **On Look At Start ()** (Quando viene rivolto lo sguardo all'inizio)</span><span class="sxs-lookup"><span data-stu-id="a1d13-139">In the **On Look At Start ()** event section</span></span>
  * <span data-ttu-id="a1d13-140">Fare clic sull'icona **+** piccola per aggiungere un altro evento</span><span class="sxs-lookup"><span data-stu-id="a1d13-140">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="a1d13-141">Assegnare l'oggetto, ad esempio lo stesso oggetto **TextMeshPro**, al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="a1d13-141">Assign the object itself, i.e. the same **TextMeshPro** object, to the **None (Object)** field</span></span>
  * <span data-ttu-id="a1d13-142">Dall'elenco a discesa **No Function** (Nessuna funzione) selezionare **TextMeshPro** > **float fontSize** (fontSize mobile) per aggiornare il valore della proprietà quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="a1d13-142">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="a1d13-143">Impostare l'argomento su **0,06** per aumentare del 50% le dimensioni correnti del carattere 0,04</span><span class="sxs-lookup"><span data-stu-id="a1d13-143">Set the argument to **0.06** to increase the current font size of 0.04 by 50%</span></span>
* <span data-ttu-id="a1d13-144">Nella sezione dell'evento **On Look Away ()** (Quando viene distolto lo sguardo)</span><span class="sxs-lookup"><span data-stu-id="a1d13-144">In the **On Look Away ()** event section</span></span>
  * <span data-ttu-id="a1d13-145">Fare clic sull'icona **+** piccola per aggiungere un altro evento</span><span class="sxs-lookup"><span data-stu-id="a1d13-145">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="a1d13-146">Assegnare l'oggetto, ad esempio lo stesso oggetto **TextMeshPro**, al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="a1d13-146">Assign the object itself, i.e. the same **TextMeshPro** object, to the **None (Object)** field</span></span>
  * <span data-ttu-id="a1d13-147">Dall'elenco a discesa **No Function** (Nessuna funzione) selezionare **TextMeshPro** > **float fontSize** (fontSize mobile) per aggiornare il valore della proprietà quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="a1d13-147">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="a1d13-148">Impostare l'argomento su **0,04** per ripristinare le dimensioni del carattere a 0,04</span><span class="sxs-lookup"><span data-stu-id="a1d13-148">Set the argument to **0.04** to reset the font size back to 0.04</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-3.png)

<span data-ttu-id="a1d13-150">**Ripetere** questo passaggio per l'oggetto **Explode** (Espandi) > SeeItSayItLabel > **TextMeshPro** e l'oggetto **Reset** (Ripristina) > SeeItSayItLabel > **TextMeshPro**.</span><span class="sxs-lookup"><span data-stu-id="a1d13-150">**Repeat** this step for the **Explode** > SeeItSayItLabel > **TextMeshPro** object and the **Reset** > SeeItSayItLabel > **TextMeshPro** object.</span></span>

<span data-ttu-id="a1d13-151">Se si immette la modalità di gioco e quindi si tiene premuto il pulsante destro del mouse mentre si sposta il puntatore del mouse fino a quando lo sguardo fisso raggiunge una delle etichette, si noterà che le dimensioni del carattere aumentano del 50% e vengono ripristinate le dimensioni originali quando si distoglie lo sguardo:</span><span class="sxs-lookup"><span data-stu-id="a1d13-151">If you now enter Game mode and then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the labels, you will see the font size increase by 50% and reset back to its original size when looking away:</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="a1d13-153">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="a1d13-153">Congratulations</span></span>

<span data-ttu-id="a1d13-154">In questa esercitazione si è appreso come abilitare il tracciamento oculare per HoloLens 2 e come aggiungere questa funzionalità agli oggetti per attivare le azioni quando l'utente rivolge loro lo sguardo.</span><span class="sxs-lookup"><span data-stu-id="a1d13-154">In this tutorial, you learned how to enable eye-tracking for HoloLens 2 and how to add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

[<span data-ttu-id="a1d13-155">Esercitazione successiva: 9. Uso dei comandi vocali</span><span class="sxs-lookup"><span data-stu-id="a1d13-155">Next Tutorial: 9. Using speech commands</span></span>](mr-learning-base-09.md)
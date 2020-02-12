---
title: Esercitazioni introduttive-6. Esplorazione delle opzioni di input avanzate
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 18bcbc95746a2e66b88d83f279603aa7f171bbcb
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129662"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="b589e-105">6. esplorazione delle opzioni di input avanzate</span><span class="sxs-lookup"><span data-stu-id="b589e-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="b589e-106">In questa esercitazione si esamineranno alcune opzioni di input avanzate per HoloLens 2, tra cui l'uso di comandi vocali, movimenti di panoramica e rilevamento degli occhi.</span><span class="sxs-lookup"><span data-stu-id="b589e-106">In this tutorial, you will explore a few advanced input options for HoloLens 2, including the use of voice commands, panning gesture, and eye tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="b589e-107">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="b589e-107">Objectives</span></span>

* <span data-ttu-id="b589e-108">Attivare eventi usando comandi vocali e parole chiave</span><span class="sxs-lookup"><span data-stu-id="b589e-108">Trigger events using voice commands and keywords</span></span>
* <span data-ttu-id="b589e-109">Usare le mani tracciate per la panoramica delle trame e degli oggetti 3D con le mani rilevate</span><span class="sxs-lookup"><span data-stu-id="b589e-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
* <span data-ttu-id="b589e-110">Sfruttare le funzionalità di rilevamento degli occhi di HoloLens 2 per selezionare gli oggetti</span><span class="sxs-lookup"><span data-stu-id="b589e-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="enabling-voice-commands"></a><span data-ttu-id="b589e-111">Abilitazione dei comandi vocali</span><span class="sxs-lookup"><span data-stu-id="b589e-111">Enabling Voice Commands</span></span>
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

<span data-ttu-id="b589e-112">In questa sezione verrà implementato un comando vocale per consentire all'utente di riprodurre un suono nell'oggetto Octa.</span><span class="sxs-lookup"><span data-stu-id="b589e-112">In this section, you will implement a speech command to let the user play a sound on the Octa object.</span></span> <span data-ttu-id="b589e-113">A tale scopo, si creerà un nuovo comando vocale e quindi si configurerà l'evento in modo da attivare l'azione desiderata quando la parola chiave del comando vocale viene pronunciata.</span><span class="sxs-lookup"><span data-stu-id="b589e-113">For this, you will create a new speech command and then configure the event so it triggers the desired action when the speech command keyword is spoken.</span></span>

<span data-ttu-id="b589e-114">Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:</span><span class="sxs-lookup"><span data-stu-id="b589e-114">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="b589e-115">Clonare il profilo di sistema di input predefinito</span><span class="sxs-lookup"><span data-stu-id="b589e-115">Clone the default Input System Profile</span></span>
2. <span data-ttu-id="b589e-116">Clonare il profilo dei comandi vocali predefiniti</span><span class="sxs-lookup"><span data-stu-id="b589e-116">Clone the default Speech Commands Profile</span></span>
3. <span data-ttu-id="b589e-117">Crea un nuovo comando vocale</span><span class="sxs-lookup"><span data-stu-id="b589e-117">Create a new speech command</span></span>
4. <span data-ttu-id="b589e-118">Aggiungere e configurare il componente gestore di input vocale (script)</span><span class="sxs-lookup"><span data-stu-id="b589e-118">Add and configure the Speech Input Handler (Script) component</span></span>
5. <span data-ttu-id="b589e-119">Implementare l'evento di risposta per il comando vocale</span><span class="sxs-lookup"><span data-stu-id="b589e-119">Implement the Response event for the speech command</span></span>

### <a name="1-clone-the-default-input-system-profile"></a><span data-ttu-id="b589e-120">1. clonare il profilo di sistema di input predefinito</span><span class="sxs-lookup"><span data-stu-id="b589e-120">1. Clone the default Input System Profile</span></span>

<span data-ttu-id="b589e-121">Nella finestra gerarchia selezionare l'oggetto **MixedRealityToolkit** , quindi nella finestra Inspector selezionare la scheda **input** e clonare il **DefaultHoloLens2InputSystemProfile** per sostituirlo con il proprio profilo di **sistema di input**personalizzabile:</span><span class="sxs-lookup"><span data-stu-id="b589e-121">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab and clone the **DefaultHoloLens2InputSystemProfile** to replace it with your own customizable **Input System Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="b589e-123">Per un promemoria su come clonare i profili MRTK, è possibile fare riferimento alle istruzioni [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) .</span><span class="sxs-lookup"><span data-stu-id="b589e-123">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

### <a name="2-clone-the-default-speech-commands-profile"></a><span data-ttu-id="b589e-124">2. clonare il profilo dei comandi vocali predefiniti</span><span class="sxs-lookup"><span data-stu-id="b589e-124">2. Clone the default Speech Commands Profile</span></span>

<span data-ttu-id="b589e-125">Espandere la sezione **sintesi vocale** e clonare il **DefaultMixedRealitySpeechCommandsProfile** per sostituirlo con un **profilo di comandi vocale**personalizzabile:</span><span class="sxs-lookup"><span data-stu-id="b589e-125">Expand the **Speech** section and clone the **DefaultMixedRealitySpeechCommandsProfile** to replace it with your own customizable **Speech Commands Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a><span data-ttu-id="b589e-127">3. creare un nuovo comando vocale</span><span class="sxs-lookup"><span data-stu-id="b589e-127">3. Create a new speech command</span></span>

<span data-ttu-id="b589e-128">Nella sezione **comandi vocali** fare clic sul pulsante **+ Aggiungi un nuovo riconoscimento** vocale per aggiungere un nuovo comando vocale nella parte inferiore dell'elenco dei comandi di riconoscimento vocale esistenti, quindi nel campo **parola chiave** immettere una parola o una frase appropriata, ad esempio **Play Music**:</span><span class="sxs-lookup"><span data-stu-id="b589e-128">In the **Speech Commands** section, click the **+ Add a New Speech Command** button to add a new speech command to the bottom of the list of existing speech commands, then in the **Keyword** field enter a suitable word or phrase, for example **Play Music**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> <span data-ttu-id="b589e-130">Se il computer non dispone di un microfono e si vuole testare il comando vocale usando la simulazione in-Editor, è possibile assegnare un KeyCode al comando vocale che consente di attivarlo quando viene premuto il tasto corrispondente.</span><span class="sxs-lookup"><span data-stu-id="b589e-130">If your computer doesn't have a microphone and you would like to test the speech command using the in-editor simulation, you can assign a KeyCode to the speech command which will let you trigger it when the corresponding key is pressed.</span></span>

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a><span data-ttu-id="b589e-131">4. aggiungere e configurare il componente gestore di input vocale (script)</span><span class="sxs-lookup"><span data-stu-id="b589e-131">4. Add and configure the Speech Input Handler (Script) component</span></span>

<span data-ttu-id="b589e-132">Nella finestra gerarchia selezionare l'oggetto **Octa** e aggiungere il componente **gestore di input vocale (script)** all'oggetto Octa.</span><span class="sxs-lookup"><span data-stu-id="b589e-132">In the Hierarchy window, select the **Octa** object and add the **Speech Input Handler (Script)** component to the Octa object.</span></span> <span data-ttu-id="b589e-133">Deselezionare quindi la casella di controllo **è stato attivo obbligatorio** in modo che l'utente non debba esaminare l'oggetto Octa per attivare il comando vocale:</span><span class="sxs-lookup"><span data-stu-id="b589e-133">Then uncheck the **Is Focus Required** checkbox so the user is not required to look at the Octa object to trigger the speech command:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a><span data-ttu-id="b589e-135">5. implementare l'evento di risposta per il comando vocale</span><span class="sxs-lookup"><span data-stu-id="b589e-135">5. Implement the Response event for the speech command</span></span>

<span data-ttu-id="b589e-136">Nel componente gestore di input vocale (script) fare clic sul pulsante **+** piccolo per aggiungere una parola chiave e quindi, dall'elenco a discesa **parola chiave** , scegliere la parola chiave **Play Music** creata in precedenza:</span><span class="sxs-lookup"><span data-stu-id="b589e-136">On the Speech Input Handler (Script) component, click the small **+** button to add a keyword, and then, from the **Keyword** dropdown, choose the **Play Music** keyword you created earlier:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="b589e-138">Le parole chiave nell'elenco a discesa della parola chiave vengono popolate in base alle parole chiave definite nell'elenco dei comandi vocali nel profilo dei comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="b589e-138">The keywords in the Keyword dropdown are populated based on the keywords defined in the Speech Commands list in the Speech Commands Profile.</span></span>

<span data-ttu-id="b589e-139">Creare un nuovo evento **Response ()** , configurare l'oggetto **Octa** per ricevere l'evento, definire **audiosource. PlayOneShot** come azione da attivare e assegnare una clip audio adatta al campo **clip** audio, ad esempio, il MRTK_Gem clip audio:</span><span class="sxs-lookup"><span data-stu-id="b589e-139">Create a new **Response ()** event, configure the **Octa** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!TIP]
> <span data-ttu-id="b589e-141">Per un promemoria sulla modalità di implementazione degli eventi e sull'assegnazione di un clip audio, è possibile fare riferimento alle istruzioni per l'esecuzione di per l' [evento Touch started](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) .</span><span class="sxs-lookup"><span data-stu-id="b589e-141">For a reminder on how to implement events and assign an audio clip, you can refer to the [Implement the On Touch Started event](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) instructions.</span></span>

## <a name="the-pan-gesture"></a><span data-ttu-id="b589e-142">Il movimento di panoramica</span><span class="sxs-lookup"><span data-stu-id="b589e-142">The Pan Gesture</span></span>

<span data-ttu-id="b589e-143">Il gesto Pan è utile per lo scorrimento usando il dito o la mano per scorrere il contenuto.</span><span class="sxs-lookup"><span data-stu-id="b589e-143">The pan gesture is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="b589e-144">In questo esempio si apprenderà innanzitutto come scorrere un'interfaccia utente 2D e quindi espanderla in modo da poter scorrere una raccolta di oggetti 3D.</span><span class="sxs-lookup"><span data-stu-id="b589e-144">In this example, you will first learn how to scroll a 2D UI and then expand on that to be able to scroll through a collection of 3D objects.</span></span>

<span data-ttu-id="b589e-145">Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:</span><span class="sxs-lookup"><span data-stu-id="b589e-145">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="b589e-146">Creare un oggetto Quad che può essere usato per la panoramica</span><span class="sxs-lookup"><span data-stu-id="b589e-146">Create a Quad object that can be used for panning</span></span>
2. <span data-ttu-id="b589e-147">Aggiungere il componente near Interaction touchable (script)</span><span class="sxs-lookup"><span data-stu-id="b589e-147">Add the Near Interaction Touchable (Script) component</span></span>
3. <span data-ttu-id="b589e-148">Aggiungere il componente zoom (script) per l'interazione della mano</span><span class="sxs-lookup"><span data-stu-id="b589e-148">Add the Hand Interaction Pan Zoom (Script) component</span></span>
4. <span data-ttu-id="b589e-149">Aggiungere contenuto 2D da scorrere</span><span class="sxs-lookup"><span data-stu-id="b589e-149">Add 2D content to be scrolled</span></span>
5. <span data-ttu-id="b589e-150">Aggiungi contenuto 3D da scorrere</span><span class="sxs-lookup"><span data-stu-id="b589e-150">Add 3D content to be scrolled</span></span>
6. <span data-ttu-id="b589e-151">Aggiungere il componente Move with Pan (script)</span><span class="sxs-lookup"><span data-stu-id="b589e-151">Add the Move With Pan (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="b589e-152">Il componente Move with Pan (script) non fa parte di MRTK.</span><span class="sxs-lookup"><span data-stu-id="b589e-152">The Move With Pan (Script) component is not part of MRTK.</span></span> <span data-ttu-id="b589e-153">È stato fornito con le risorse dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="b589e-153">It was provided with this tutorial's assets.</span></span>

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a><span data-ttu-id="b589e-154">1. creare un oggetto Quad che può essere usato per la panoramica</span><span class="sxs-lookup"><span data-stu-id="b589e-154">1. Create a Quad object that can be used for panning</span></span>

<span data-ttu-id="b589e-155">Nella finestra gerarchia, fare clic con il pulsante destro del mouse su un'area vuota e selezionare **oggetto 3d** > **Quad** per aggiungere un quad alla scena.</span><span class="sxs-lookup"><span data-stu-id="b589e-155">In the Hierarchy window, right-click at an empty area and select **3D Object** > **Quad** to add a quad to your scene.</span></span> <span data-ttu-id="b589e-156">Assegnare un nome appropriato, ad esempio **PanGesture**, e posizionarlo in una posizione appropriata, ad esempio X = 0, Y =-0,2, Z = 2.</span><span class="sxs-lookup"><span data-stu-id="b589e-156">Give it a suitable name, for example, **PanGesture**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="b589e-158">Per un promemoria su come aggiungere alla scena le primitive Unity, ad esempio un Quad 3D, è possibile fare riferimento alle istruzioni [aggiungere un cubo alla scena](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) .</span><span class="sxs-lookup"><span data-stu-id="b589e-158">For a reminder on how to add Unity primitives, such as a 3D quad, to your scene, you can refer to the [Add a cube to the scene](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) instructions.</span></span>

<span data-ttu-id="b589e-159">Come per qualsiasi altra interazione, il movimento Pan richiede anche un Collider.</span><span class="sxs-lookup"><span data-stu-id="b589e-159">As with any other interaction, the the pan gesture also requires a collider.</span></span> <span data-ttu-id="b589e-160">Per impostazione predefinita, un quad ha un Collider mesh.</span><span class="sxs-lookup"><span data-stu-id="b589e-160">By default, a Quad has a mesh collider.</span></span> <span data-ttu-id="b589e-161">Tuttavia, il mesh Collider non è ideale perché è estremamente sottile.</span><span class="sxs-lookup"><span data-stu-id="b589e-161">However, the mesh collider is not ideal because it is extremely thin.</span></span> <span data-ttu-id="b589e-162">Per semplificare l'interazione dell'utente con il Collider, il mesh Collider viene sostituito con un Collider di box.</span><span class="sxs-lookup"><span data-stu-id="b589e-162">To make it easier for the user to interact with the collider, we will replace the mesh collider with a box collider.</span></span>

<span data-ttu-id="b589e-163">Con l'oggetto PanGesture ancora selezionato, fare clic sull'icona **delle impostazioni** del componente **mesh Collider** e selezionare **Rimuovi componente** per rimuovere il mesh Collider:</span><span class="sxs-lookup"><span data-stu-id="b589e-163">With the PanGesture object still selected, click the **Mesh Collider** component's **Settings** icon and select **Remove Component** to remove the Mesh Collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

<span data-ttu-id="b589e-165">Nella finestra di controllo usare il pulsante **Aggiungi componente** per aggiungere un **Collider di box**, quindi modificare le **dimensioni** di box Collider da Z a 0,15 per aumentare lo spessore della casella Collider:</span><span class="sxs-lookup"><span data-stu-id="b589e-165">In the Inspector window, use the **Add Component** button to add a **Box Collider**, then change the Box Collider **Size** Z to 0.15 to increase the thickness of the box collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a><span data-ttu-id="b589e-167">2. aggiungere il componente di prossimità interazione (script)</span><span class="sxs-lookup"><span data-stu-id="b589e-167">2. Add the Near Interaction Touchable (Script) component</span></span>

<span data-ttu-id="b589e-168">Se l'oggetto **PanGesture** è ancora selezionato, aggiungere il componente **near Interaction (script)** per l'oggetto PanGesture, quindi fare clic sui pulsanti **Correggi limiti** e **Correggi centro** per aggiornare le proprietà del centro locale e dei limiti di near Interaction touchable (script) in modo che corrispondano a BoxCollider:</span><span class="sxs-lookup"><span data-stu-id="b589e-168">With the **PanGesture** object still selected, add the **Near Interaction Touchable (Script)** component to the PanGesture object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a><span data-ttu-id="b589e-170">3. aggiungere il componente zoom (script) per l'interazione della mano</span><span class="sxs-lookup"><span data-stu-id="b589e-170">3. Add the Hand Interaction Pan Zoom (Script) component</span></span>

<span data-ttu-id="b589e-171">Con l'oggetto **PanGesture** ancora selezionato, aggiungere il componente **Zoom Pan (script)** per l'interazione con la mano all'oggetto PanGesture e quindi selezionare la casella di controllo **blocca orizzontalmente** per consentire solo lo scorrimento verticale:</span><span class="sxs-lookup"><span data-stu-id="b589e-171">With the **PanGesture** object still selected, add the **Hand Interaction Pan Zoom (Script)** component to the PanGesture object, and then check the **Lock Horizontal** checkbox to allow vertical scrolling only:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a><span data-ttu-id="b589e-173">4. aggiungere contenuto 2D da scorrere</span><span class="sxs-lookup"><span data-stu-id="b589e-173">4. Add 2D content to be scrolled</span></span>

<span data-ttu-id="b589e-174">Nel pannello del progetto cercare il materiale **PanContent** , quindi fare clic su di esso e trascinarlo sulla proprietà elemento 0 del **materiale** renderer di mesh dell'oggetto **PanGesture** :</span><span class="sxs-lookup"><span data-stu-id="b589e-174">In the Project panel, search for the **PanContent** material and then click-and-drag it on to the **PanGesture** object's Mesh Renderer **Material** Element 0 property:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

<span data-ttu-id="b589e-176">Nella finestra di controllo espandere il componente del materiale **PanContent** appena aggiunto e quindi modificare il valore di **affiancamento** Y in 0,5 in modo che corrisponda al valore X e i riquadri siano quadrati:</span><span class="sxs-lookup"><span data-stu-id="b589e-176">In the Inspector window, expand the newly added **PanContent** material component, and then change it's **Tiling** Y value to 0.5 so it matches the X value and the tiles appear square:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

<span data-ttu-id="b589e-178">Se si immette la modalità di gioco, è possibile eseguire il test dello scorrimento del contenuto 2D usando il gesto della panoramica nella simulazione dell'Editor:</span><span class="sxs-lookup"><span data-stu-id="b589e-178">If you now enter Game mode, you can test scrolling the 2D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a><span data-ttu-id="b589e-180">5. aggiungere il contenuto 3D da scorrere</span><span class="sxs-lookup"><span data-stu-id="b589e-180">5. Add 3D content to be scrolled</span></span>

<span data-ttu-id="b589e-181">Nella finestra gerarchia **creare quattro cubi** come oggetti figlio di **PanContent** e impostare la relativa **scala** di trasformazione su X = 0,15, Y = 0,15, Z = 0,15:</span><span class="sxs-lookup"><span data-stu-id="b589e-181">In the Hierarchy window, **create four cubes** as a child objects of the **PanContent** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

<span data-ttu-id="b589e-183">Per spaziare i cubi in modo uniforme e risparmiare tempo, aggiungere il componente Grid Object Collection (script) all'oggetto padre Cubes, ad esempio l'oggetto PanGesture, e configurare la raccolta di oggetti Grid (script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="b589e-183">To space the cubes out evenly, and save some time, add the Grid Object Collection (Script) component, to the cubes' parent object, i.e. the PanGesture object, and configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="b589e-184">Modificare **num Rows** su 1 in modo che tutti i cubi siano allineati in una singola riga</span><span class="sxs-lookup"><span data-stu-id="b589e-184">Change **Num Rows** to 1 to have all the cubes aligned on one single row</span></span>
* <span data-ttu-id="b589e-185">Modificare la **larghezza della cella** a 0,25 per spaziare i cubi all'interno della riga</span><span class="sxs-lookup"><span data-stu-id="b589e-185">Change **Cell Width** to 0.25 to space out the cubes within the row</span></span>

<span data-ttu-id="b589e-186">Quindi fare clic sul pulsante **Aggiorna raccolta** per applicare la nuova configurazione:</span><span class="sxs-lookup"><span data-stu-id="b589e-186">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a><span data-ttu-id="b589e-188">6. aggiungere il componente Move with Pan (script)</span><span class="sxs-lookup"><span data-stu-id="b589e-188">6. Add the Move With Pan (Script) component</span></span>

<span data-ttu-id="b589e-189">Nella finestra gerarchia selezionare tutti gli **oggetti figlio del cubo**, quindi nella finestra di controllo usare il pulsante **Aggiungi componente** per aggiungere il componente **spostamento con panoramica (script)** a tutti i cubi:</span><span class="sxs-lookup"><span data-stu-id="b589e-189">In the Hierarchy window, select all the **Cube child objects**, then in the Inspector window, use the **Add Component** button to add the **Move With Pan (Script)** component to all the cubes:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> <span data-ttu-id="b589e-191">Per un promemoria sulla selezione di più oggetti nella finestra gerarchia, le condizioni possono fare riferimento al [componente Aggiungi il gestore di manipolazione (script) a tutte le istruzioni per gli oggetti](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) .</span><span class="sxs-lookup"><span data-stu-id="b589e-191">For a reminder on how to select multiple objects in the Hierarchy window, tou can refer to the [Add the Manipulation Handler (Script) component to all the objects](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) instructions.</span></span>

<span data-ttu-id="b589e-192">Con tutti i cubi ancora selezionati, fare clic e trascinare l'oggetto **PanGesture** nel campo **origine input Pan** :</span><span class="sxs-lookup"><span data-stu-id="b589e-192">With all the cubes still selected, click-and-drag the **PanGesture** object to the **Pan Input Source** field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> <span data-ttu-id="b589e-194">Il componente spostamento con Pan (script) in ogni cubo è in ascolto dell'evento di aggiornamento della panoramica inviato dal componente HandInteractionPanZoom (script) nell'oggetto PanGesture, assegnato come origine di input Pan nel passaggio precedente, e aggiorna la posizione di ogni cubo. conseguenza.</span><span class="sxs-lookup"><span data-stu-id="b589e-194">The Move With Pan (Script) component on each cube listens for the Pan Updated event sent by the HandInteractionPanZoom (Script) component on the PanGesture object, which you assigned as the Pan Input Source in the step above, and updates each cube's position accordingly.</span></span>

<span data-ttu-id="b589e-195">Nella finestra gerarchia selezionare l'oggetto **PanGesture** , quindi nella casella di controllo **deseleziona** il **renderer mesh** per disabilitare il componente renderer mesh:</span><span class="sxs-lookup"><span data-stu-id="b589e-195">In the Hierarchy window, select the **PanGesture** object, then in the inspector **un-check** the **Mesh Renderer** checkbox to disable the Mesh Renderer component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

<span data-ttu-id="b589e-197">Se si immette la modalità di gioco, è possibile eseguire il test dello scorrimento del contenuto 3D usando il gesto della panoramica nella simulazione dell'Editor:</span><span class="sxs-lookup"><span data-stu-id="b589e-197">If you now enter Game mode, you can test scrolling the 3D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a><span data-ttu-id="b589e-199">Tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="b589e-199">Eye Tracking</span></span>

<span data-ttu-id="b589e-200">In questa sezione si esaminerà come abilitare il rilevamento degli occhi nel progetto.</span><span class="sxs-lookup"><span data-stu-id="b589e-200">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="b589e-201">Per questo esempio, si implementerà la funzionalità per fare in modo che ogni oggetto nel 3DObjectCollection si avvii lentamente mentre viene esaminato dallo sguardo dell'utente, nonché attivare un effetto blip quando l'oggetto da esaminare è selezionato tramite il tocco di aria o il comando vocale.</span><span class="sxs-lookup"><span data-stu-id="b589e-201">For this example, you will implement functionality to make each object in the 3DObjectCollection spin slowly while being looked at by the user's eye gaze, as well as, trigger a blip effect when the object being looked at is selected by air-tap or speech command.</span></span>

<span data-ttu-id="b589e-202">Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:</span><span class="sxs-lookup"><span data-stu-id="b589e-202">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="b589e-203">Aggiungere il componente della destinazione di rilevamento degli occhi (script) a tutti gli oggetti di destinazione</span><span class="sxs-lookup"><span data-stu-id="b589e-203">Add the Eye Tracking Target (Script) component to all target objects</span></span>
2. <span data-ttu-id="b589e-204">Aggiungere il componente Demo dell'esercitazione per la verifica degli occhi (script) a tutti gli oggetti di destinazione</span><span class="sxs-lookup"><span data-stu-id="b589e-204">Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>
3. <span data-ttu-id="b589e-205">Implementare l'oggetto durante la ricerca dell'evento di destinazione</span><span class="sxs-lookup"><span data-stu-id="b589e-205">Implement the While Looking At Target event</span></span>
4. <span data-ttu-id="b589e-206">Implementa l'evento selezionato</span><span class="sxs-lookup"><span data-stu-id="b589e-206">Implement the On Selected event</span></span>
5. <span data-ttu-id="b589e-207">Abilitare la verifica degli occhi simulati per le simulazioni in-Editor</span><span class="sxs-lookup"><span data-stu-id="b589e-207">Enable simulated eye tracking for in-editor simulations</span></span>
6. <span data-ttu-id="b589e-208">Abilitare l'input dello sguardo nelle funzionalità dell'app del progetto di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b589e-208">Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a><span data-ttu-id="b589e-209">1. aggiungere il componente della destinazione di rilevamento degli occhi (script) a tutti gli oggetti di destinazione</span><span class="sxs-lookup"><span data-stu-id="b589e-209">1. Add the Eye Tracking Target (Script) component to all target objects</span></span>

<span data-ttu-id="b589e-210">Nella finestra gerarchia espandere l'oggetto **3DObjectCollection** e selezionare tutti gli **oggetti figlio**, quindi nella finestra di controllo usare il pulsante **Aggiungi componente** per aggiungere il componente di **destinazione di rilevamento degli occhi (script)** a tutti gli oggetti figlio:</span><span class="sxs-lookup"><span data-stu-id="b589e-210">In the Hierarchy window, expand the **3DObjectCollection** object and select all the **child objects**, then in the Inspector window, use the **Add Component** button to add the **Eye Tracking Target (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

<span data-ttu-id="b589e-212">Con tutti gli **oggetti figlio** ancora selezionati, configurare il componente di **destinazione del rilevamento degli occhi (script)** come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="b589e-212">With all the **child objects** still selected, configure the **Eye Tracking Target (Script)** component as follows:</span></span>

* <span data-ttu-id="b589e-213">Modificare selezionare l' **azione** da **selezionare**per definire l'azione di tocco aereo per questo oggetto come SELECT</span><span class="sxs-lookup"><span data-stu-id="b589e-213">Change **Select Action** to **Select**, to define the air-tap action for this object as Select</span></span>
* <span data-ttu-id="b589e-214">Espandere **voce selezionare** e impostare le **dimensioni** dell'elenco dei comandi vocali su 1 e quindi, nell'elenco nuovo elemento visualizzato, modificare l' **elemento 0** in **Seleziona**per definire l'azione del comando vocale per questo oggetto come SELECT</span><span class="sxs-lookup"><span data-stu-id="b589e-214">Expand **Voice Select** and set the voice command list **Size** to 1, and then, in the new element list that appear, change **Element 0** to **Select**, to define the speech command action for this object as Select</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a><span data-ttu-id="b589e-216">2. aggiungere il componente Demo dell'esercitazione per la verifica degli occhi (script) a tutti gli oggetti di destinazione</span><span class="sxs-lookup"><span data-stu-id="b589e-216">2. Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>

<span data-ttu-id="b589e-217">Con tutti gli **oggetti figlio** ancora selezionati, usare il pulsante **Aggiungi componente** per aggiungere il componente Demo dell'esercitazione per la **Verifica degli occhi (script)** a tutti gli oggetti figlio:</span><span class="sxs-lookup"><span data-stu-id="b589e-217">With all the **child objects** still selected, use the **Add Component** button to add the **Eye Tracking Tutorial Demo (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> <span data-ttu-id="b589e-219">Il componente della destinazione di rilevamento degli occhi (script) non fa parte di MRTK.</span><span class="sxs-lookup"><span data-stu-id="b589e-219">The Eye Tracking Target (Script) component is not part of MRTK.</span></span> <span data-ttu-id="b589e-220">È stato fornito con le risorse dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="b589e-220">It was provided with this tutorial's assets.</span></span>

### <a name="3-implement-the-while-looking-at-target-event"></a><span data-ttu-id="b589e-221">3. implementare durante la ricerca dell'evento di destinazione</span><span class="sxs-lookup"><span data-stu-id="b589e-221">3. Implement the While Looking At Target event</span></span>

<span data-ttu-id="b589e-222">Nella finestra gerarchia selezionare l'oggetto **Cheese** , quindi creare un nuovo oggetto durante la ricerca dell'evento **target ()** , configurare l'oggetto **Cheese** per ricevere l'evento e definire **EyeTrackingTutorialDemo. RotateTarget** come azione da attivare:</span><span class="sxs-lookup"><span data-stu-id="b589e-222">In the Hierarchy window, select the **Cheese** object, then create a new **While Looking At Target ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

<span data-ttu-id="b589e-224">**Ripetere** per ogni oggetto figlio in 3DObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="b589e-224">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

> [!TIP]
> <span data-ttu-id="b589e-225">Per un promemoria su come implementare gli eventi, è possibile fare riferimento alle istruzioni per i [movimenti di rilevamento della mano e i pulsanti interagiscono](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) .</span><span class="sxs-lookup"><span data-stu-id="b589e-225">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="4-implement-the-on-selected-event"></a><span data-ttu-id="b589e-226">4. implementare nell'evento selezionato</span><span class="sxs-lookup"><span data-stu-id="b589e-226">4. Implement the On Selected event</span></span>

<span data-ttu-id="b589e-227">Nella finestra gerarchia selezionare l'oggetto **Cheese** , quindi creare un nuovo evento **on Selected ()** , configurare l'oggetto **Cheese** per ricevere l'evento e definire **EyeTrackingTutorialDemo. RotateTarget** come azione da attivare:</span><span class="sxs-lookup"><span data-stu-id="b589e-227">In the Hierarchy window, select the **Cheese** object, then create a new **On Selected ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

<span data-ttu-id="b589e-229">**Ripetere** per ogni oggetto figlio in 3DObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="b589e-229">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a><span data-ttu-id="b589e-230">5. abilitare la verifica degli occhi simulati per le simulazioni in-Editor</span><span class="sxs-lookup"><span data-stu-id="b589e-230">5. Enable simulated eye tracking for in-editor simulations</span></span>

<span data-ttu-id="b589e-231">Nella finestra gerarchia selezionare l'oggetto **MixedRealityToolkit** , quindi nella finestra di controllo selezionare la scheda **input** , espandere la sezione provider di **dati di input** e quindi la sezione del **servizio di simulazione input** e clonare il **DefaultMixedRealityInputSimulationProfile** per sostituirlo con il profilo di **simulazione di input**personalizzabile:</span><span class="sxs-lookup"><span data-stu-id="b589e-231">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab, expand the **Input Data Providers** section and then the **Input Simulation Service** section, and clone the **DefaultMixedRealityInputSimulationProfile** to replace it with your own customizable **Input Simulation Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> <span data-ttu-id="b589e-233">Per un promemoria su come clonare i profili MRTK, è possibile fare riferimento alle istruzioni [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) .</span><span class="sxs-lookup"><span data-stu-id="b589e-233">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="b589e-234">Nella sezione **simulazione degli** occhi, selezionare la casella di controllo **simula la posizione degli** occhi per abilitare la simulazione di rilevamento degli occhi:</span><span class="sxs-lookup"><span data-stu-id="b589e-234">In the **Eye Simulation** section, check the **Simulate Eye Position** checkbox to enable eye tracking simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

<span data-ttu-id="b589e-236">Se si immette la modalità di gioco, è possibile testare gli effetti di rotazione e di selezione implementati regolando la visualizzazione in modo che il cursore raggiunga uno degli oggetti e usando il comando interazione mano o riconoscimento vocale per selezionare l'oggetto:</span><span class="sxs-lookup"><span data-stu-id="b589e-236">If you now enter Game mode, you can test the spin and blip effects you implemented by adjusting the view so the cursor hits one of the objects and using hand interaction or speech command to select the object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> <span data-ttu-id="b589e-238">Se non è stato usato DefaultHoloLens2ConfigurationProfile per clonare il profilo di configurazione MRTK personalizzabile, come indicato nelle istruzioni [configurare il Toolkit per la realtà mista](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) , la verifica degli occhi potrebbe non essere abilitata nel progetto e sarà necessario abilitarla.</span><span class="sxs-lookup"><span data-stu-id="b589e-238">If you did not use the DefaultHoloLens2ConfigurationProfile to clone your customizable MRTK configuration profile, as instructed in the [Configure the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) instructions, eye tracking may not be enable in your project and will need to be enabled.</span></span> <span data-ttu-id="b589e-239">A tale proposito, è possibile fare riferimento alla [Guida introduttiva a Eye Tracking nelle istruzioni di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) .</span><span class="sxs-lookup"><span data-stu-id="b589e-239">For that, you can refer to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions.</span></span>

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a><span data-ttu-id="b589e-240">6. abilitare l'input dello sguardo nelle funzionalità dell'app del progetto di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b589e-240">6. Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

<span data-ttu-id="b589e-241">Prima di compilare e distribuire l'app da Visual Studio al dispositivo, è necessario abilitare l'input dello sguardo nelle funzionalità dell'app del progetto.</span><span class="sxs-lookup"><span data-stu-id="b589e-241">Before building and deploying your app from Visual Studio to your device, Gaze Input has to been enabled in the project's app capabilities.</span></span> <span data-ttu-id="b589e-242">A tale proposito, è possibile seguire le istruzioni per [testare l'app Unity in un HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) .</span><span class="sxs-lookup"><span data-stu-id="b589e-242">For this, you can follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="b589e-243">Complimenti</span><span class="sxs-lookup"><span data-stu-id="b589e-243">Congratulations</span></span>

<span data-ttu-id="b589e-244">Sono state aggiunte le funzionalità di base per la verifica degli occhi all'applicazione.</span><span class="sxs-lookup"><span data-stu-id="b589e-244">You have successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="b589e-245">Queste azioni sono solo l'inizio del vasto mondo di possibilità offerte dal tracciamento oculare.</span><span class="sxs-lookup"><span data-stu-id="b589e-245">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="b589e-246">In questa esercitazione sono state illustrate anche altre funzionalità di input avanzate, ad esempio i comandi vocali e i movimenti di panoramica.</span><span class="sxs-lookup"><span data-stu-id="b589e-246">In this tutorial, you also learned about other advanced input features, such as voice commands and panning gestures.</span></span>

[<span data-ttu-id="b589e-247">Lezione successiva: 7. creazione di un'applicazione di esempio del modulo Lunar</span><span class="sxs-lookup"><span data-stu-id="b589e-247">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)

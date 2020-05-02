---
title: Esercitazioni introduttive - 6. Esplorazione delle opzioni di input avanzate
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: ec078015304e1cddc9b042fb5e94cf1904a302cb
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2020
ms.locfileid: "79376088"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="7f111-105">6. Esplorazione delle opzioni di input avanzate</span><span class="sxs-lookup"><span data-stu-id="7f111-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="7f111-106">In questa esercitazione esaminerai alcune opzioni di input avanzate per HoloLens 2, come l'uso di comandi vocali, il movimento di panoramica e il tracciamento oculare.</span><span class="sxs-lookup"><span data-stu-id="7f111-106">In this tutorial, you will explore a few advanced input options for HoloLens 2, including the use of voice commands, panning gesture, and eye tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="7f111-107">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="7f111-107">Objectives</span></span>

* <span data-ttu-id="7f111-108">Attivare gli eventi usando comandi vocali e parole chiave</span><span class="sxs-lookup"><span data-stu-id="7f111-108">Trigger events using voice commands and keywords</span></span>
* <span data-ttu-id="7f111-109">Usare le mani tracciate per fare una panoramica di trame e oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="7f111-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
* <span data-ttu-id="7f111-110">Sfruttare le funzionalità di tracciamento oculare di HoloLens 2 per selezionare gli oggetti</span><span class="sxs-lookup"><span data-stu-id="7f111-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="enabling-voice-commands"></a><span data-ttu-id="7f111-111">Abilitazione dei comandi vocali</span><span class="sxs-lookup"><span data-stu-id="7f111-111">Enabling Voice Commands</span></span>
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

<span data-ttu-id="7f111-112">In questa sezione implementerai un comando vocale per consentire all'utente di riprodurre un suono per l'oggetto Octa.</span><span class="sxs-lookup"><span data-stu-id="7f111-112">In this section, you will implement a speech command to let the user play a sound on the Octa object.</span></span> <span data-ttu-id="7f111-113">A tale scopo, creerai un nuovo comando vocale e quindi configurerai l'evento in modo che attivi l'azione desiderata quando viene pronunciata la parola chiave del comando vocale.</span><span class="sxs-lookup"><span data-stu-id="7f111-113">For this, you will create a new speech command and then configure the event so it triggers the desired action when the speech command keyword is spoken.</span></span>

<span data-ttu-id="7f111-114">Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:</span><span class="sxs-lookup"><span data-stu-id="7f111-114">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="7f111-115">Clonare il profilo di sistema di input predefinito</span><span class="sxs-lookup"><span data-stu-id="7f111-115">Clone the default Input System Profile</span></span>
2. <span data-ttu-id="7f111-116">Clonare il profilo dei comandi vocali predefinito</span><span class="sxs-lookup"><span data-stu-id="7f111-116">Clone the default Speech Commands Profile</span></span>
3. <span data-ttu-id="7f111-117">Creare un nuovo comando vocale</span><span class="sxs-lookup"><span data-stu-id="7f111-117">Create a new speech command</span></span>
4. <span data-ttu-id="7f111-118">Aggiungere e configurare il componente Speech Input Handler (Script) (Gestore input vocale - Script)</span><span class="sxs-lookup"><span data-stu-id="7f111-118">Add and configure the Speech Input Handler (Script) component</span></span>
5. <span data-ttu-id="7f111-119">Implementare l'evento Response (Risposta) per il comando vocale</span><span class="sxs-lookup"><span data-stu-id="7f111-119">Implement the Response event for the speech command</span></span>

### <a name="1-clone-the-default-input-system-profile"></a><span data-ttu-id="7f111-120">1. Clonare il profilo di sistema di input predefinito</span><span class="sxs-lookup"><span data-stu-id="7f111-120">1. Clone the default Input System Profile</span></span>

<span data-ttu-id="7f111-121">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) seleziona la scheda **Input** e clona **DefaultHoloLens2InputSystemProfile** per sostituirlo con il tuo **profilo di sistema di input** personalizzabile:</span><span class="sxs-lookup"><span data-stu-id="7f111-121">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab and clone the **DefaultHoloLens2InputSystemProfile** to replace it with your own customizable **Input System Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="7f111-123">Per rivedere la procedura di clonazione dei profili MRTK, puoi fare riferimento alle istruzioni contenute in [Come configurare i profili di Mixed Reality Toolkit](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option).</span><span class="sxs-lookup"><span data-stu-id="7f111-123">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

### <a name="2-clone-the-default-speech-commands-profile"></a><span data-ttu-id="7f111-124">2. Clonare il profilo dei comandi vocali predefinito</span><span class="sxs-lookup"><span data-stu-id="7f111-124">2. Clone the default Speech Commands Profile</span></span>

<span data-ttu-id="7f111-125">Espandi la sezione **Speech** (Voce) e clona **DefaultMixedRealitySpeechCommandsProfile** per sostituirlo con il tuo **profilo dei comandi vocali** personalizzabile:</span><span class="sxs-lookup"><span data-stu-id="7f111-125">Expand the **Speech** section and clone the **DefaultMixedRealitySpeechCommandsProfile** to replace it with your own customizable **Speech Commands Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a><span data-ttu-id="7f111-127">3. Creare un nuovo comando vocale</span><span class="sxs-lookup"><span data-stu-id="7f111-127">3. Create a new speech command</span></span>

<span data-ttu-id="7f111-128">Nella sezione **Speech Commands** (Comandi vocali) fai clic sul pulsante **+ Add a New Speech Command** (+ Aggiungi un nuovo comando vocale) per aggiungere un nuovo comando vocale in fondo all'elenco dei comandi vocali esistenti e quindi nel campo **Keyword** (Parola chiave) immetti una parola o una frase appropriata, ad esempio **Play Music** (Riproduci musica):</span><span class="sxs-lookup"><span data-stu-id="7f111-128">In the **Speech Commands** section, click the **+ Add a New Speech Command** button to add a new speech command to the bottom of the list of existing speech commands, then in the **Keyword** field enter a suitable word or phrase, for example **Play Music**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> <span data-ttu-id="7f111-130">Se il computer non dispone di un microfono e vuoi provare il comando vocale usando la simulazione nell'editor, puoi assegnare un codice tasto (KeyCode) al comando vocale in modo che tale comando venga attivato quando viene premuto il tasto corrispondente.</span><span class="sxs-lookup"><span data-stu-id="7f111-130">If your computer doesn't have a microphone and you would like to test the speech command using the in-editor simulation, you can assign a KeyCode to the speech command which will let you trigger it when the corresponding key is pressed.</span></span>

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a><span data-ttu-id="7f111-131">4. Aggiungere e configurare il componente Speech Input Handler (Script) (Gestore input vocale - Script)</span><span class="sxs-lookup"><span data-stu-id="7f111-131">4. Add and configure the Speech Input Handler (Script) component</span></span>

<span data-ttu-id="7f111-132">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Octa** e aggiungigli il componente **Speech Input Handler (Script)** (Gestore input vocale - Script).</span><span class="sxs-lookup"><span data-stu-id="7f111-132">In the Hierarchy window, select the **Octa** object and add the **Speech Input Handler (Script)** component to the Octa object.</span></span> <span data-ttu-id="7f111-133">Quindi deseleziona la casella di controllo **Is Focus Required** (È necessario lo stato attivo) in modo che l'utente non debba guardare l'oggetto Octa per attivare il comando vocale:</span><span class="sxs-lookup"><span data-stu-id="7f111-133">Then uncheck the **Is Focus Required** checkbox so the user is not required to look at the Octa object to trigger the speech command:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a><span data-ttu-id="7f111-135">5. Implementare l'evento Response (Risposta) per il comando vocale</span><span class="sxs-lookup"><span data-stu-id="7f111-135">5. Implement the Response event for the speech command</span></span>

<span data-ttu-id="7f111-136">Nel componente Speech Input Handler (Script) (Gestore input vocale - Script) fai clic sul piccolo pulsante **+** per aggiungere un elemento parola chiave all'elenco delle parole chiave:</span><span class="sxs-lookup"><span data-stu-id="7f111-136">On the Speech Input Handler (Script) component, click the small **+** button to add a keyword element to the list of keywords:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

<span data-ttu-id="7f111-138">Fai clic sull'**Element 0** (Elemento 0) appena creato per espanderlo e quindi dall'elenco a discesa **Keyword** (Parola chiave) seleziona la parola chiave **Play Music** (Riproduci musica) creata in precedenza:</span><span class="sxs-lookup"><span data-stu-id="7f111-138">Click the newly created **Element 0** to expand it, and then, from the **Keyword** dropdown, choose the **Play Music** keyword you created earlier:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> <span data-ttu-id="7f111-140">L'elenco a discesa Keyword (Parola chiave) viene popolato con le parole chiave definite nell'elenco Speech Commands (Comandi vocali) nel profilo dei comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="7f111-140">The keywords in the Keyword dropdown are populated based on the keywords defined in the Speech Commands list in the Speech Commands Profile.</span></span>

<span data-ttu-id="7f111-141">Crea un nuovo evento **Response ()** (Risposta), configura l'oggetto **Octa** in modo che riceva l'evento, definisci **AudioSource.PlayOneShot** come azione da attivare e assegna un clip audio appropriato al campo **Audio Clip** (Clip audio), ad esempio MRTK_Gem:</span><span class="sxs-lookup"><span data-stu-id="7f111-141">Create a new **Response ()** event, configure the **Octa** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> <span data-ttu-id="7f111-143">Per rivedere la procedura di implementazione degli eventi e di assegnazione di un clip audio, puoi fare riferimento alle istruzioni contenute in [Implementare l'evento On Touch Started (Avviato al tocco)](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event).</span><span class="sxs-lookup"><span data-stu-id="7f111-143">For a reminder on how to implement events and assign an audio clip, you can refer to the [Implement the On Touch Started event](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) instructions.</span></span>

## <a name="the-pan-gesture"></a><span data-ttu-id="7f111-144">Il movimento di panoramica</span><span class="sxs-lookup"><span data-stu-id="7f111-144">The Pan Gesture</span></span>

<span data-ttu-id="7f111-145">Il movimento di panoramica è utile per le operazioni di scorrimento del contenuto tramite il dito o la mano.</span><span class="sxs-lookup"><span data-stu-id="7f111-145">The pan gesture is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="7f111-146">In questo esempio apprenderai innanzitutto come scorrere un'interfaccia utente 2D e quindi come espanderla in modo da poter scorrere una raccolta di oggetti 3D.</span><span class="sxs-lookup"><span data-stu-id="7f111-146">In this example, you will first learn how to scroll a 2D UI and then expand on that to be able to scroll through a collection of 3D objects.</span></span>

<span data-ttu-id="7f111-147">Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:</span><span class="sxs-lookup"><span data-stu-id="7f111-147">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="7f111-148">Creare un oggetto Quad utilizzabile per la panoramica</span><span class="sxs-lookup"><span data-stu-id="7f111-148">Create a Quad object that can be used for panning</span></span>
2. <span data-ttu-id="7f111-149">Aggiungere il componente Near Interaction Touchable (Script) (Toccabile con interazione da vicino - Script)</span><span class="sxs-lookup"><span data-stu-id="7f111-149">Add the Near Interaction Touchable (Script) component</span></span>
3. <span data-ttu-id="7f111-150">Aggiungere il componente Hand Interaction Pan Zoom (Script) (Zoom panoramica con interazione manuale - Script)</span><span class="sxs-lookup"><span data-stu-id="7f111-150">Add the Hand Interaction Pan Zoom (Script) component</span></span>
4. <span data-ttu-id="7f111-151">Aggiungere il contenuto 2D da scorrere</span><span class="sxs-lookup"><span data-stu-id="7f111-151">Add 2D content to be scrolled</span></span>
5. <span data-ttu-id="7f111-152">Aggiungere il contenuto 3D da scorrere</span><span class="sxs-lookup"><span data-stu-id="7f111-152">Add 3D content to be scrolled</span></span>
6. <span data-ttu-id="7f111-153">Aggiungere il componente Move With Pan (Script) (Spostamento con panoramica - Script)</span><span class="sxs-lookup"><span data-stu-id="7f111-153">Add the Move With Pan (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="7f111-154">Il componente Move With Pan (Script) (Spostamento con panoramica - Script) non fa parte di MRTK.</span><span class="sxs-lookup"><span data-stu-id="7f111-154">The Move With Pan (Script) component is not part of MRTK.</span></span> <span data-ttu-id="7f111-155">È stato fornito con gli asset dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="7f111-155">It was provided with this tutorial's assets.</span></span>

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a><span data-ttu-id="7f111-156">1. Creare un oggetto Quad utilizzabile per la panoramica</span><span class="sxs-lookup"><span data-stu-id="7f111-156">1. Create a Quad object that can be used for panning</span></span>

<span data-ttu-id="7f111-157">Nella finestra Hierarchy (Gerarchia) fai clic con il pulsante destro del mouse su un'area vuota e scegli **3D Object** (Oggetto 3D) > **Quad** per aggiungere un quadrilatero alla scena.</span><span class="sxs-lookup"><span data-stu-id="7f111-157">In the Hierarchy window, right-click at an empty area and select **3D Object** > **Quad** to add a quad to your scene.</span></span> <span data-ttu-id="7f111-158">Assegnagli un nome appropriato, ad esempio **PanGesture**, e collocalo in una posizione adatta, ad esempio X = 0, Y = -0.2, Z = 2.</span><span class="sxs-lookup"><span data-stu-id="7f111-158">Give it a suitable name, for example, **PanGesture**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="7f111-160">Per rivedere come aggiungere alla scena i primitivi di Unity, ad esempio un quadrilatero 3D, puoi fare riferimento alle istruzioni contenute in [Aggiungere un cubo alla scena](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene).</span><span class="sxs-lookup"><span data-stu-id="7f111-160">For a reminder on how to add Unity primitives, such as a 3D quad, to your scene, you can refer to the [Add a cube to the scene](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) instructions.</span></span>

<span data-ttu-id="7f111-161">Come qualsiasi altra interazione, anche il movimento di panoramica richiede un collisore.</span><span class="sxs-lookup"><span data-stu-id="7f111-161">As with any other interaction, the the pan gesture also requires a collider.</span></span> <span data-ttu-id="7f111-162">Per impostazione predefinita, un oggetto Quad ha un collisore mesh.</span><span class="sxs-lookup"><span data-stu-id="7f111-162">By default, a Quad has a mesh collider.</span></span> <span data-ttu-id="7f111-163">Tuttavia, questo tipo di collisore non è ideale perché è estremamente sottile.</span><span class="sxs-lookup"><span data-stu-id="7f111-163">However, the mesh collider is not ideal because it is extremely thin.</span></span> <span data-ttu-id="7f111-164">Per facilitare l'interazione tra l'utente e il collisore, il collisore mesh verrà sostituito con un collisore cuboide.</span><span class="sxs-lookup"><span data-stu-id="7f111-164">To make it easier for the user to interact with the collider, we will replace the mesh collider with a box collider.</span></span>

<span data-ttu-id="7f111-165">Con l'oggetto PanGesture ancora selezionato, fai clic sull'icona delle **impostazioni** del componente **Mesh Collider** (Collisore mesh) e seleziona **Remove Component** (Rimuovi componente) per rimuovere il collisore mesh:</span><span class="sxs-lookup"><span data-stu-id="7f111-165">With the PanGesture object still selected, click the **Mesh Collider** component's **Settings** icon and select **Remove Component** to remove the Mesh Collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

<span data-ttu-id="7f111-167">Nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere un **Box Collider** (Collisore cuboide) e quindi imposta su 0.15 il valore Z di **Size** (Dimensioni) per rendere più spesso tale collisore:</span><span class="sxs-lookup"><span data-stu-id="7f111-167">In the Inspector window, use the **Add Component** button to add a **Box Collider**, then change the Box Collider **Size** Z to 0.15 to increase the thickness of the box collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a><span data-ttu-id="7f111-169">2. Aggiungere il componente Near Interaction Touchable (Script) (Toccabile con interazione da vicino - Script)</span><span class="sxs-lookup"><span data-stu-id="7f111-169">2. Add the Near Interaction Touchable (Script) component</span></span>

<span data-ttu-id="7f111-170">Con l'oggetto **PanGesture** ancora selezionato, aggiungigli il componente **Near Interaction Touchable (Script)** (Toccabile con interazione da vicino - Script) e quindi fai clic sui pulsanti **Fix Bounds** (Correggi limiti) e **Fix Center** (Correggi centro) per aggiornare le proprietà relative ai limiti e al centro in locale di tale componente in modo che corrispondano a BoxCollider:</span><span class="sxs-lookup"><span data-stu-id="7f111-170">With the **PanGesture** object still selected, add the **Near Interaction Touchable (Script)** component to the PanGesture object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a><span data-ttu-id="7f111-172">3. Aggiungere il componente Hand Interaction Pan Zoom (Script) (Zoom panoramica con interazione manuale - Script)</span><span class="sxs-lookup"><span data-stu-id="7f111-172">3. Add the Hand Interaction Pan Zoom (Script) component</span></span>

<span data-ttu-id="7f111-173">Con l'oggetto **PanGesture** ancora selezionato, aggiungigli il componente **Hand Interaction Pan Zoom (Script)** (Zoom panoramica con interazione manuale - Script) e quindi seleziona la casella di controllo **Lock Horizontal** (Blocca in orizzontale) per consentire solo lo scorrimento verticale:</span><span class="sxs-lookup"><span data-stu-id="7f111-173">With the **PanGesture** object still selected, add the **Hand Interaction Pan Zoom (Script)** component to the PanGesture object, and then check the **Lock Horizontal** checkbox to allow vertical scrolling only:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a><span data-ttu-id="7f111-175">4. Aggiungere il contenuto 2D da scorrere</span><span class="sxs-lookup"><span data-stu-id="7f111-175">4. Add 2D content to be scrolled</span></span>

<span data-ttu-id="7f111-176">Nel pannello Project (Progetto) cerca il materiale **PanContent** e quindi fai clic e trascinalo sulla proprietà Element 0 (Elemento 0) in **Materials** (Materiali) nella sezione Mesh Renderer (Renderer mesh) dell'oggetto **PanGesture**:</span><span class="sxs-lookup"><span data-stu-id="7f111-176">In the Project panel, search for the **PanContent** material and then click-and-drag it on to the **PanGesture** object's Mesh Renderer **Material** Element 0 property:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

<span data-ttu-id="7f111-178">Nella finestra Inspector (Controllo) espandi il componente materiale **PanContent** appena aggiunto e quindi imposta su 0.5 il valore Y di **Tiling** (Affiancamento) in modo che corrisponda al valore X e i riquadri risultino quadrati:</span><span class="sxs-lookup"><span data-stu-id="7f111-178">In the Inspector window, expand the newly added **PanContent** material component, and then change it's **Tiling** Y value to 0.5 so it matches the X value and the tiles appear square:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

<span data-ttu-id="7f111-180">Se ora passi alla modalità di gioco, puoi provare lo scorrimento del contenuto 2D usando il movimento di panoramica nella simulazione nell'editor:</span><span class="sxs-lookup"><span data-stu-id="7f111-180">If you now enter Game mode, you can test scrolling the 2D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a><span data-ttu-id="7f111-182">5. Aggiungere il contenuto 3D da scorrere</span><span class="sxs-lookup"><span data-stu-id="7f111-182">5. Add 3D content to be scrolled</span></span>

<span data-ttu-id="7f111-183">Nella finestra Hierarchy (Gerarchia) **crea quattro cubi** come oggetti figlio dell'oggetto **PanGesture** e in Transform (Trasformazione) imposta **Scale** (Scala) su X = 0.15, Y = 0.15, Z = 0.15:</span><span class="sxs-lookup"><span data-stu-id="7f111-183">In the Hierarchy window, **create four cubes** as a child objects of the **PanGesture** object and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

<span data-ttu-id="7f111-185">Per spaziare i cubi in modo uniforme e risparmiare tempo, aggiungi il componente **Grid Object Collection (Script)** (Raccolta oggetti griglia - Script) all'oggetto padre dei cubi, ovvero all'oggetto **PanGesture**, e configura il componente come segue:</span><span class="sxs-lookup"><span data-stu-id="7f111-185">To space the cubes out evenly, and save some time, add the **Grid Object Collection (Script)** component, to the cubes' parent object, i.e. the **PanGesture** object, and configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="7f111-186">Imposta **Num Rows** (Numero di righe) su 1 per avere tutti i cubi allineati in una sola riga</span><span class="sxs-lookup"><span data-stu-id="7f111-186">Change **Num Rows** to 1 to have all the cubes aligned on one single row</span></span>
* <span data-ttu-id="7f111-187">Imposta **Cell Width** (Larghezza cella) su 0.25 per spaziare i cubi all'interno della riga</span><span class="sxs-lookup"><span data-stu-id="7f111-187">Change **Cell Width** to 0.25 to space out the cubes within the row</span></span>

<span data-ttu-id="7f111-188">Fai quindi clic sul pulsante **Update Collection** (Aggiorna raccolta) per applicare la nuova configurazione:</span><span class="sxs-lookup"><span data-stu-id="7f111-188">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a><span data-ttu-id="7f111-190">6. Aggiungere il componente Move With Pan (Script) (Spostamento con panoramica - Script)</span><span class="sxs-lookup"><span data-stu-id="7f111-190">6. Add the Move With Pan (Script) component</span></span>

<span data-ttu-id="7f111-191">Nella finestra Hierarchy (Gerarchia) seleziona tutti gli **oggetti figlio Cube** e quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Move With Pan (Script)** (Spostamento con panoramica - Script) a tutti i cubi:</span><span class="sxs-lookup"><span data-stu-id="7f111-191">In the Hierarchy window, select all the **Cube child objects**, then in the Inspector window, use the **Add Component** button to add the **Move With Pan (Script)** component to all the cubes:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> <span data-ttu-id="7f111-193">Per rivedere la procedura di selezione di più oggetti nella finestra Hierarchy (Gerarchia), puoi fare riferimento alle istruzioni contenute in [Aggiungere il componente Manipulation Handler (Script) (Gestore manipolazione - Script) a tutti gli oggetti](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects).</span><span class="sxs-lookup"><span data-stu-id="7f111-193">For a reminder on how to select multiple objects in the Hierarchy window, tou can refer to the [Add the Manipulation Handler (Script) component to all the objects](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) instructions.</span></span>

<span data-ttu-id="7f111-194">Con tutti i cubi selezionati, fai clic e trascina l'oggetto **PanGesture** sul campo **Pan Input Source** (Origine input panoramica):</span><span class="sxs-lookup"><span data-stu-id="7f111-194">With all the cubes still selected, click-and-drag the **PanGesture** object to the **Pan Input Source** field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> <span data-ttu-id="7f111-196">Il component Move With Pan (Script) (Spostamento con panoramica - Script) di ogni cubo resta in ascolto dell'evento Pan Updated (Aggiornato con panoramica) inviato dal componente HandInteractionPanZoom (Script) nell'oggetto PanGesture, assegnato come origine input panoramica nel passaggio precedente, e aggiorna di conseguenza la posizione di ciascun cubo.</span><span class="sxs-lookup"><span data-stu-id="7f111-196">The Move With Pan (Script) component on each cube listens for the Pan Updated event sent by the HandInteractionPanZoom (Script) component on the PanGesture object, which you assigned as the Pan Input Source in the step above, and updates each cube's position accordingly.</span></span>

<span data-ttu-id="7f111-197">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **PanGesture** e quindi nella finestra Inspector (Controllo) **deseleziona** la casella di controllo **Mesh Renderer** (Renderer mesh) per disabilitare tale renderer:</span><span class="sxs-lookup"><span data-stu-id="7f111-197">In the Hierarchy window, select the **PanGesture** object, then in the inspector **un-check** the **Mesh Renderer** checkbox to disable the Mesh Renderer component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

<span data-ttu-id="7f111-199">Se ora passi alla modalità di gioco, puoi provare lo scorrimento del contenuto 3D usando il movimento di panoramica nella simulazione nell'editor:</span><span class="sxs-lookup"><span data-stu-id="7f111-199">If you now enter Game mode, you can test scrolling the 3D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a><span data-ttu-id="7f111-201">Tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="7f111-201">Eye Tracking</span></span>

<span data-ttu-id="7f111-202">In questa sezione esaminerai come abilitare il tracciamento oculare nel tuo progetto.</span><span class="sxs-lookup"><span data-stu-id="7f111-202">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="7f111-203">Per questo esempio, implementerai la funzionalità in modo da far ruotare lentamente ogni oggetto incluso nella raccolta 3DObjectCollection mentre l'utente posa su di esso uno sguardo fisso e in modo che venga attivato un effetto sonoro quando l'oggetto guardato viene selezionato tramite simulazione del tocco o comando vocale.</span><span class="sxs-lookup"><span data-stu-id="7f111-203">For this example, you will implement functionality to make each object in the 3DObjectCollection spin slowly while being looked at by the user's eye gaze, as well as, trigger a blip effect when the object being looked at is selected by air-tap or speech command.</span></span>

<span data-ttu-id="7f111-204">Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:</span><span class="sxs-lookup"><span data-stu-id="7f111-204">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="7f111-205">Aggiungere il componente Eye Tracking Target (Script) (Destinazione tracciamento oculare - Script) a tutti gli oggetti di destinazione</span><span class="sxs-lookup"><span data-stu-id="7f111-205">Add the Eye Tracking Target (Script) component to all target objects</span></span>
2. <span data-ttu-id="7f111-206">Aggiungere il componente Eye Tracking Tutorial Demo (Script) (Demo esercitazione tracciamento oculare - Script) a tutti gli oggetti di destinazione</span><span class="sxs-lookup"><span data-stu-id="7f111-206">Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>
3. <span data-ttu-id="7f111-207">Implementare l'evento While Looking At Target (Mentre viene guardata la destinazione)</span><span class="sxs-lookup"><span data-stu-id="7f111-207">Implement the While Looking At Target event</span></span>
4. <span data-ttu-id="7f111-208">Implementare l'evento On Selected (Alla selezione)</span><span class="sxs-lookup"><span data-stu-id="7f111-208">Implement the On Selected event</span></span>
5. <span data-ttu-id="7f111-209">Abilitare il tracciamento oculare simulato per le simulazioni nell'editor</span><span class="sxs-lookup"><span data-stu-id="7f111-209">Enable simulated eye tracking for in-editor simulations</span></span>
6. <span data-ttu-id="7f111-210">Abilitare l'input sguardo fisso nelle funzionalità dell'app del progetto di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7f111-210">Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a><span data-ttu-id="7f111-211">1. Aggiungere il componente Eye Tracking Target (Script) (Destinazione tracciamento oculare - Script) a tutti gli oggetti di destinazione</span><span class="sxs-lookup"><span data-stu-id="7f111-211">1. Add the Eye Tracking Target (Script) component to all target objects</span></span>

<span data-ttu-id="7f111-212">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **3DObjectCollection** e seleziona tutti gli **oggetti figlio**, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Eye Tracking Target (Script)** (Destinazione tracciamento oculare - Script) a tutti gli oggetti figlio:</span><span class="sxs-lookup"><span data-stu-id="7f111-212">In the Hierarchy window, expand the **3DObjectCollection** object and select all the **child objects**, then in the Inspector window, use the **Add Component** button to add the **Eye Tracking Target (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

<span data-ttu-id="7f111-214">Con tutti gli **oggetti figlio** ancora selezionati, configura il componente **Eye Tracking Target (Script)** (Destinazione tracciamento oculare - Script) come segue:</span><span class="sxs-lookup"><span data-stu-id="7f111-214">With all the **child objects** still selected, configure the **Eye Tracking Target (Script)** component as follows:</span></span>

* <span data-ttu-id="7f111-215">Imposta **Select Action** (Seleziona azione) su **Select** (Seleziona) per definire la selezione come azione di simulazione del tocco per questo oggetto</span><span class="sxs-lookup"><span data-stu-id="7f111-215">Change **Select Action** to **Select**, to define the air-tap action for this object as Select</span></span>
* <span data-ttu-id="7f111-216">Espandi **Voice Select** (Selezione vocale) e imposta su 1 il valore **Size** (Dimensioni) dell'elenco dei comandi vocali e quindi nel nuovo elenco di elementi che viene visualizzato imposta **Element 0** (Elemento 0) su **Select** (Seleziona) per definire la selezione come azione del comando vocale per questo oggetto</span><span class="sxs-lookup"><span data-stu-id="7f111-216">Expand **Voice Select** and set the voice command list **Size** to 1, and then, in the new element list that appear, change **Element 0** to **Select**, to define the speech command action for this object as Select</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a><span data-ttu-id="7f111-218">2. Aggiungere il componente Eye Tracking Tutorial Demo (Script) (Demo esercitazione tracciamento oculare - Script) a tutti gli oggetti di destinazione</span><span class="sxs-lookup"><span data-stu-id="7f111-218">2. Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>

<span data-ttu-id="7f111-219">Con tutti gli **oggetti figlio** ancora selezionati, usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Eye Tracking Tutorial Demo (Script)** (Demo esercitazione tracciamento oculare - Script) a tutti gli oggetti figlio:</span><span class="sxs-lookup"><span data-stu-id="7f111-219">With all the **child objects** still selected, use the **Add Component** button to add the **Eye Tracking Tutorial Demo (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> <span data-ttu-id="7f111-221">Il componente Eye Tracking Target (Script) (Destinazione tracciamento oculare - Script) non fa parte di MRTK.</span><span class="sxs-lookup"><span data-stu-id="7f111-221">The Eye Tracking Target (Script) component is not part of MRTK.</span></span> <span data-ttu-id="7f111-222">È stato fornito con gli asset dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="7f111-222">It was provided with this tutorial's assets.</span></span>

### <a name="3-implement-the-while-looking-at-target-event"></a><span data-ttu-id="7f111-223">3. Implementare l'evento While Looking At Target (Mentre viene guardata la destinazione)</span><span class="sxs-lookup"><span data-stu-id="7f111-223">3. Implement the While Looking At Target event</span></span>

<span data-ttu-id="7f111-224">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Cheese** e quindi crea un nuovo evento **While Looking At Target ()** (Mentre viene guardata la destinazione), configura l'oggetto **Cheese** in modo che riceva l'evento e definisci **EyeTrackingTutorialDemo.RotateTarget** come azione da attivare:</span><span class="sxs-lookup"><span data-stu-id="7f111-224">In the Hierarchy window, select the **Cheese** object, then create a new **While Looking At Target ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

<span data-ttu-id="7f111-226">**Ripeti** per ogni oggetto figlio incluso in 3DObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="7f111-226">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

> [!TIP]
> <span data-ttu-id="7f111-227">Per rivedere la procedura di implementazione degli eventi, puoi fare riferimento alle istruzioni contenute in [Movimenti di tracciamento della mano e pulsanti con supporto per interazioni](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).</span><span class="sxs-lookup"><span data-stu-id="7f111-227">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="4-implement-the-on-selected-event"></a><span data-ttu-id="7f111-228">4. Implementare l'evento On Selected (Alla selezione)</span><span class="sxs-lookup"><span data-stu-id="7f111-228">4. Implement the On Selected event</span></span>

<span data-ttu-id="7f111-229">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Cheese** e quindi crea un nuovo evento **On Selected ()** (Alla selezione), configura l'oggetto **Cheese** in modo che riceva l'evento e definisci **EyeTrackingTutorialDemo.BlipTarget** come azione da attivare:</span><span class="sxs-lookup"><span data-stu-id="7f111-229">In the Hierarchy window, select the **Cheese** object, then create a new **On Selected ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.BlipTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

<span data-ttu-id="7f111-231">**Ripeti** per ogni oggetto figlio incluso in 3DObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="7f111-231">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a><span data-ttu-id="7f111-232">5. Abilitare il tracciamento oculare simulato per le simulazioni nell'editor</span><span class="sxs-lookup"><span data-stu-id="7f111-232">5. Enable simulated eye tracking for in-editor simulations</span></span>

<span data-ttu-id="7f111-233">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **MixedRealityToolkit**, quindi nella finestra Inspector (Controllo) seleziona la scheda **Input**, espandi la sezione **Input Data Providers** (Provider di dati di input) e poi la sezione **Input Simulation Service** (Servizio di simulazione input) e infine clona **DefaultMixedRealityInputSimulationProfile** per sostituirlo con il tuo **profilo di simulazione input** personalizzabile:</span><span class="sxs-lookup"><span data-stu-id="7f111-233">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab, expand the **Input Data Providers** section and then the **Input Simulation Service** section, and clone the **DefaultMixedRealityInputSimulationProfile** to replace it with your own customizable **Input Simulation Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> <span data-ttu-id="7f111-235">Per rivedere la procedura di clonazione dei profili MRTK, puoi fare riferimento alle istruzioni contenute in [Come configurare i profili di Mixed Reality Toolkit](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option).</span><span class="sxs-lookup"><span data-stu-id="7f111-235">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="7f111-236">Nella sezione **Eye Simulation** (Simulazione oculare) seleziona la casella di controllo **Simulate Eye Position** (Simula posizione oculare) per abilitare la simulazione del tracciamento oculare:</span><span class="sxs-lookup"><span data-stu-id="7f111-236">In the **Eye Simulation** section, check the **Simulate Eye Position** checkbox to enable eye tracking simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

<span data-ttu-id="7f111-238">Se ora passi alla modalità di gioco, puoi provare l'effetto di rotazione e quello sonoro implementati adattando la vista in modo che il cursore tocchi uno degli oggetti e usando l'interazione con la mano o il comando vocale per selezionare l'oggetto:</span><span class="sxs-lookup"><span data-stu-id="7f111-238">If you now enter Game mode, you can test the spin and blip effects you implemented by adjusting the view so the cursor hits one of the objects and using hand interaction or speech command to select the object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> <span data-ttu-id="7f111-240">Se non hai usato DefaultHoloLens2ConfigurationProfile per clonare il tuo profilo di configurazione MRTK personalizzabile, come illustrato in [Configurare Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit), il tracciamento oculare potrebbe non essere abilitato nel tuo progetto e dovrà essere abilitato.</span><span class="sxs-lookup"><span data-stu-id="7f111-240">If you did not use the DefaultHoloLens2ConfigurationProfile to clone your customizable MRTK configuration profile, as instructed in the [Configure the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) instructions, eye tracking may not be enable in your project and will need to be enabled.</span></span> <span data-ttu-id="7f111-241">A tale scopo, puoi fare riferimento alle istruzioni contenute in [Introduzione al tracciamento oculare in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html).</span><span class="sxs-lookup"><span data-stu-id="7f111-241">For that, you can refer to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions.</span></span>

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a><span data-ttu-id="7f111-242">6. Abilitare l'input sguardo fisso nelle funzionalità dell'app del progetto di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7f111-242">6. Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

<span data-ttu-id="7f111-243">Prima di compilare e distribuire l'app da Visual Studio nel dispositivo, è necessario abilitare l'input sguardo fisso nelle funzionalità dell'app del progetto.</span><span class="sxs-lookup"><span data-stu-id="7f111-243">Before building and deploying your app from Visual Studio to your device, Gaze Input has to been enabled in the project's app capabilities.</span></span> <span data-ttu-id="7f111-244">A tale scopo, puoi seguire le istruzioni contenute in [Test dell'app Unity su un dispositivo HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="7f111-244">For this, you can follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="7f111-245">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="7f111-245">Congratulations</span></span>

<span data-ttu-id="7f111-246">Hai ora aggiunto alla tua applicazione le funzionalità di base per il tracciamento oculare.</span><span class="sxs-lookup"><span data-stu-id="7f111-246">You have successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="7f111-247">Queste azioni sono solo l'inizio del vasto mondo di possibilità offerte dal tracciamento oculare.</span><span class="sxs-lookup"><span data-stu-id="7f111-247">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="7f111-248">In questa esercitazione hai anche avuto informazioni su altre funzionalità di input avanzate, ad esempio i comandi vocali e i movimenti di panoramica.</span><span class="sxs-lookup"><span data-stu-id="7f111-248">In this tutorial, you also learned about other advanced input features, such as voice commands and panning gestures.</span></span>

[<span data-ttu-id="7f111-249">Lezione successiva: 7. Creazione dell'applicazione di esempio Lunar Module</span><span class="sxs-lookup"><span data-stu-id="7f111-249">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)

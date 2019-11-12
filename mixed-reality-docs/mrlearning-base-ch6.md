---
title: Esercitazioni introduttive-7. Creazione di un'applicazione di esempio del modulo Lunar
description: In questa lezione vengono combinati più concetti appresi dalle lezioni precedenti per creare un'esperienza di esempio univoca.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: b033e4f9a379fb1778da3d94da70262e073d141b
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926514"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="72fdb-105">7. creazione di un'applicazione di esempio del modulo Lunar</span><span class="sxs-lookup"><span data-stu-id="72fdb-105">7. Creating a Lunar Module sample application</span></span>

<span data-ttu-id="72fdb-106">In questa esercitazione vengono combinati più concetti rispetto alle lezioni precedenti per creare un'esperienza di esempio univoca.</span><span class="sxs-lookup"><span data-stu-id="72fdb-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="72fdb-107">Si apprenderà come creare un'applicazione di assembly del modulo lunare, in base alla quale un utente deve usare le mani registrate per prelevare parti del modulo lunari e provare a assemblare un modulo lunare.</span><span class="sxs-lookup"><span data-stu-id="72fdb-107">You will learn how to create a lunar module assembly application whereby a user needs to use tracked hands to pick up lunar module parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="72fdb-108">Usiamo i pulsanti stampabili per impostare gli hint di posizionamento, per reimpostare l'esperienza e per avviare il modulo lunare nello spazio.</span><span class="sxs-lookup"><span data-stu-id="72fdb-108">We use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="72fdb-109">Nelle esercitazioni future si continuerà a sviluppare questa esperienza, che include potenti casi d'uso multiutente che sfruttano gli ancoraggi spaziali di Azure per l'allineamento spaziale.</span><span class="sxs-lookup"><span data-stu-id="72fdb-109">In future tutorials, we will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="72fdb-110">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="72fdb-110">Objectives</span></span>

- <span data-ttu-id="72fdb-111">Combinare i vari concetti illustrati nelle lezioni precedenti per creare un'esperienza unica</span><span class="sxs-lookup"><span data-stu-id="72fdb-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="72fdb-112">Apprendere come attivare o disattivare gli oggetti</span><span class="sxs-lookup"><span data-stu-id="72fdb-112">Learn how to toggle objects</span></span>
- <span data-ttu-id="72fdb-113">Attivare eventi complessi usando i pulsanti a pressione</span><span class="sxs-lookup"><span data-stu-id="72fdb-113">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="72fdb-114">Usare la forza e la fisica dei corpi rigidi</span><span class="sxs-lookup"><span data-stu-id="72fdb-114">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="72fdb-115">Esplorare l'uso delle descrizioni comandi</span><span class="sxs-lookup"><span data-stu-id="72fdb-115">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="72fdb-116">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="72fdb-116">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="72fdb-117">Configurazione del modulo lunare</span><span class="sxs-lookup"><span data-stu-id="72fdb-117">Configuring the Lunar Module</span></span>

<span data-ttu-id="72fdb-118">In questa sezione vengono introdotti i vari componenti necessari per creare l'esperienza di esempio.</span><span class="sxs-lookup"><span data-stu-id="72fdb-118">In this section, we introduce the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="72fdb-119">Aggiungere il prefabbricato dell'assembly del modulo Lunar alla scena di base.</span><span class="sxs-lookup"><span data-stu-id="72fdb-119">Add the Lunar Module Assembly prefab to your base scene.</span></span> <span data-ttu-id="72fdb-120">A tale scopo, nella scheda progetto passare a Asset > BaseModuleAssets > prefabbricates.</span><span class="sxs-lookup"><span data-stu-id="72fdb-120">To do this, in the Project tab navigate to Assets > BaseModuleAssets > Prefabs.</span></span> <span data-ttu-id="72fdb-121">Si vedranno due prefabbricati di lanciarazzi, trascinando il razzo Launcher_Tutorial prefabbricato nella scena e posizionando come desiderato.</span><span class="sxs-lookup"><span data-stu-id="72fdb-121">You will see two rocket launcher prefabs, drag the Rocket Launcher_Tutorial prefab into your scene, and position as you wish.</span></span>

    >[!NOTE]
    ><span data-ttu-id="72fdb-122">Il Rocket Launcher_Complete prefabbricato è l'utilità di avvio completata, fornita come riferimento.</span><span class="sxs-lookup"><span data-stu-id="72fdb-122">The Rocket Launcher_Complete prefab is the completed launcher, provided for reference.</span></span>

    ![Immagine lezione 6 capitolo 1 passaggio 1](images/Lesson6_Chapter1_step1im.PNG)

    <span data-ttu-id="72fdb-124">Se si espande l'oggetto gioco Rocket Launcher_Tutorial nella gerarchia e si espande ulteriormente l'oggetto Lunar Module, si troveranno diversi oggetti figlio con un materiale denominato "x-ray".</span><span class="sxs-lookup"><span data-stu-id="72fdb-124">If you expand the Rocket Launcher_Tutorial game object in your hierarchy and further expand the Lunar Module object, you find several child objects that have a material called "x-ray."</span></span> <span data-ttu-id="72fdb-125">Il materiale "x-ray" consente un colore leggermente trasparente che verrà usato come hint di selezione host per l'utente.</span><span class="sxs-lookup"><span data-stu-id="72fdb-125">The "x-ray" material allows for a slightly translucent color that will be used as placement hints for the user.</span></span> 

    ![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG)

    <span data-ttu-id="72fdb-127">Sono disponibili cinque parti per il modulo Lunar con cui l'utente interagirà, come illustrato nell'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="72fdb-127">There are five parts to the lunar module that the user will interact with, as shown in the image below:</span></span>

    1. <span data-ttu-id="72fdb-128">Scocca del rover</span><span class="sxs-lookup"><span data-stu-id="72fdb-128">The Rover Enclosure</span></span>
    2. <span data-ttu-id="72fdb-129">Serbatoio del carburante</span><span class="sxs-lookup"><span data-stu-id="72fdb-129">The Fuel Tank</span></span>
    3. <span data-ttu-id="72fdb-130">Cella energetica</span><span class="sxs-lookup"><span data-stu-id="72fdb-130">The Energy Cell</span></span>
    4. <span data-ttu-id="72fdb-131">Portale di ancoraggio</span><span class="sxs-lookup"><span data-stu-id="72fdb-131">The Docking Portal</span></span>
    5. <span data-ttu-id="72fdb-132">Sensore esterno</span><span class="sxs-lookup"><span data-stu-id="72fdb-132">The External sensor</span></span>

    ![Immagine lezione 6 capitolo 1 nota b](images/Lesson6_Chapter1_notebim.PNG)

    >[!NOTE]
    ><span data-ttu-id="72fdb-134">i nomi degli oggetti gioco visualizzati nella gerarchia della scena di base non corrispondono ai nomi degli oggetti nella scena.</span><span class="sxs-lookup"><span data-stu-id="72fdb-134">The game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

2. <span data-ttu-id="72fdb-135">Aggiungere un'origine audio all'oggetto gioco LunarModule.</span><span class="sxs-lookup"><span data-stu-id="72fdb-135">Add an audio source to the LunarModule game object.</span></span> <span data-ttu-id="72fdb-136">Assicurarsi che LunarModule sia selezionato nella gerarchia della scena e fare clic su Aggiungi componente.</span><span class="sxs-lookup"><span data-stu-id="72fdb-136">Make sure the LunarModule is selected in your scene hierarchy and click Add Component.</span></span> <span data-ttu-id="72fdb-137">Cercare l'origine audio e aggiungerla all'oggetto gioco.</span><span class="sxs-lookup"><span data-stu-id="72fdb-137">Search for Audio Source and add it to the game object.</span></span> <span data-ttu-id="72fdb-138">Lasciare vuoto il campo AudioClip per il momento, ma modificare l'impostazione speciale di Blend da 0 a 1 in modo da abilitare l'audio spaziale.</span><span class="sxs-lookup"><span data-stu-id="72fdb-138">Leave the AudioClip field blank for now, but change the Special Blend setting from 0 to 1 so to enable spatial audio.</span></span> <span data-ttu-id="72fdb-139">Questa origine audio verrà usata per riprodurre il suono di avvio in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="72fdb-139">You will use this audio source to play the launching sound later.</span></span>

    ![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG)

3. <span data-ttu-id="72fdb-141">Aggiungere gli hint per la selezione host per l'interruttore.</span><span class="sxs-lookup"><span data-stu-id="72fdb-141">Add the script Toggle Placement Hints.</span></span> <span data-ttu-id="72fdb-142">Fare clic su Aggiungi componente e cercare gli hint di selezione host.</span><span class="sxs-lookup"><span data-stu-id="72fdb-142">Click Add Component and search for Toggle Placement Hints.</span></span> <span data-ttu-id="72fdb-143">Si tratta di uno script personalizzato che consente di attivare e disattivare gli hint traslucidi (oggetti con il materiale x-ray), come indicato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="72fdb-143">This is a custom script that lets you turn on and off the translucent hints (objects with the x-ray material), as mentioned earlier.</span></span>

    ![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG)

4. <span data-ttu-id="72fdb-145">Poiché sono presenti cinque oggetti, digitare "5" per la dimensione della matrice di oggetti del gioco.</span><span class="sxs-lookup"><span data-stu-id="72fdb-145">Since we have five objects, type "5" for the game object array size.</span></span> <span data-ttu-id="72fdb-146">Verranno visualizzati cinque nuovi elementi.</span><span class="sxs-lookup"><span data-stu-id="72fdb-146">You will then see five new elements appear.</span></span>

    ![Immagine lezione 6 capitolo 1 passaggio 4b](images/Lesson6_Chapter1_step4bim.PNG)

    <span data-ttu-id="72fdb-148">Trascinare ciascuno degli oggetti traslucidi in tutte le caselle nome (oggetto gioco).</span><span class="sxs-lookup"><span data-stu-id="72fdb-148">Drag each of the translucent objects into all the Name (Game Object) boxes.</span></span> <span data-ttu-id="72fdb-149">Trascinare gli oggetti seguenti dal modulo Lunar nella scena nei campi della matrice di oggetti, come illustrato nell'immagine precedente:</span><span class="sxs-lookup"><span data-stu-id="72fdb-149">Drag the following objects from the lunar module in your scene into the object array fields as shown in the image above:</span></span>

    ![Immagine lezione 6 capitolo 1 passaggio 4a](images/Lesson6_Chapter1_step4aim.PNG)

    <span data-ttu-id="72fdb-151">Lo script di attivazione/disattivazione del posizionamento è ora configurato, che consente di attivare e disattivare i suggerimenti.</span><span class="sxs-lookup"><span data-stu-id="72fdb-151">The Toggle Placement Hints script is now configured, which allows us to turn hints on and off.</span></span>

5. <span data-ttu-id="72fdb-152">Aggiungere lo script Launch Lunar Module.</span><span class="sxs-lookup"><span data-stu-id="72fdb-152">Add the Launch Lunar Module script.</span></span> <span data-ttu-id="72fdb-153">Fare clic sul pulsante Aggiungi componente, cercare "Avvia modulo lunare" e selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="72fdb-153">Click the Add Component button, search for "launch lunar module" and select it.</span></span> <span data-ttu-id="72fdb-154">Questo script avvia il modulo Lunar.</span><span class="sxs-lookup"><span data-stu-id="72fdb-154">This script launches the lunar module.</span></span> <span data-ttu-id="72fdb-155">Quando si preme un pulsante configurato, viene aggiunta una forza ascendente al componente corpo rigido del modulo lunare e il modulo viene avviato verso l'alto.</span><span class="sxs-lookup"><span data-stu-id="72fdb-155">When we press a configured button, it adds an upward force to the lunar module's rigid body component and causes the module to launch upwards.</span></span> <span data-ttu-id="72fdb-156">In luoghi chiusi, il modulo lunare potrebbe scontrarsi contro il soffitto.</span><span class="sxs-lookup"><span data-stu-id="72fdb-156">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="72fdb-157">Se ci si trova in un'area con soffitti elevati o senza limiti, il modulo lunare si troverà nello spazio a tempo indefinito.</span><span class="sxs-lookup"><span data-stu-id="72fdb-157">If you are in an area with high ceilings or no ceilings, the lunar module will fly into space indefinitely.</span></span>

    ![Immagine lezione 6 capitolo 1 passaggio 5](images/Lesson6_Chapter1_step5im.PNG)

6. <span data-ttu-id="72fdb-159">regola la spinta in modo che il modulo lunare possa sollevarsi delicatamente.</span><span class="sxs-lookup"><span data-stu-id="72fdb-159">Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="72fdb-160">Prova con un valore pari a 0.01.</span><span class="sxs-lookup"><span data-stu-id="72fdb-160">Try a value of 0.01.</span></span> <span data-ttu-id="72fdb-161">Lascia vuoto il campo "Rb" (Cr).</span><span class="sxs-lookup"><span data-stu-id="72fdb-161">Leave the "Rb" field blank.</span></span> <span data-ttu-id="72fdb-162">RB sta per il corpo rigido e questo campo viene popolato automaticamente durante il Runtime.</span><span class="sxs-lookup"><span data-stu-id="72fdb-162">Rb stands for Rigid body and this field will be automatically populated during runtime.</span></span>

    ![Immagine lezione 6 capitolo 1 passaggio 6](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="72fdb-164">Cenni preliminari sulle parti del modulo Lunar</span><span class="sxs-lookup"><span data-stu-id="72fdb-164">Lunar Module Parts overview</span></span>

<span data-ttu-id="72fdb-165">L'oggetto padre Parts del modulo Lunar è la raccolta degli oggetti con cui l'utente interagisce.</span><span class="sxs-lookup"><span data-stu-id="72fdb-165">The Lunar Module Parts parent object is the collection of the objects that the user interacts with.</span></span> <span data-ttu-id="72fdb-166">I nomi degli oggetti di gioco con la scena con etichetta nomi racchiusi tra parentesi sono disponibili nell'elenco seguente:</span><span class="sxs-lookup"><span data-stu-id="72fdb-166">The Game object names with scene labeled names in parentheses, are provided in the list below:</span></span>

- <span data-ttu-id="72fdb-167">Zaino (cella energia)</span><span class="sxs-lookup"><span data-stu-id="72fdb-167">Backpack (Energy Cell)</span></span>
- <span data-ttu-id="72fdb-168">GASTANK Sweden (serbatoio carburante)</span><span class="sxs-lookup"><span data-stu-id="72fdb-168">GasTank (Fuel Tank)</span></span>
- <span data-ttu-id="72fdb-169">TopLeftBody (Scocca del rover)</span><span class="sxs-lookup"><span data-stu-id="72fdb-169">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="72fdb-170">Nose (Portale di ancoraggio)</span><span class="sxs-lookup"><span data-stu-id="72fdb-170">Nose (Docking Portal)</span></span>
- <span data-ttu-id="72fdb-171">LeftTwirler (Sensore esterno)</span><span class="sxs-lookup"><span data-stu-id="72fdb-171">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="72fdb-172">Si noti che ognuno di questi oggetti dispone di un gestore di manipolazione, come illustrato nella lezione 4.</span><span class="sxs-lookup"><span data-stu-id="72fdb-172">Notice that each of these objects has a manipulation handler, as explained in Lesson 4.</span></span> <span data-ttu-id="72fdb-173">Questa funzionalità consente agli utenti di acquisire e manipolare l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="72fdb-173">This feature enables users to grab and manipulate the object.</span></span> <span data-ttu-id="72fdb-174">Si noti inoltre che l'impostazione, due tipi di manipolazione gestiti, viene impostata per spostare e ruotare.</span><span class="sxs-lookup"><span data-stu-id="72fdb-174">Also note that the setting, Two Handed Manipulation Type, is set to Move and Rotate.</span></span> <span data-ttu-id="72fdb-175">Questa opzione consente solo all'utente di spostare l'oggetto e non modificarne le dimensioni, ovvero la funzionalità desiderata per un'applicazione assembly.</span><span class="sxs-lookup"><span data-stu-id="72fdb-175">This option only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="72fdb-176">Inoltre, la manipolazione a lungo è deselezionata per consentire solo l'interazione diretta delle parti del modulo.</span><span class="sxs-lookup"><span data-stu-id="72fdb-176">In addition, Far Manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Immagine lezione 6 capitolo 2](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="72fdb-178">Lo script demo dell'assembly della parte (illustrato in precedenza) è lo script che gestisce gli oggetti posizionati dall'utente sul modulo lunare dall'utente.</span><span class="sxs-lookup"><span data-stu-id="72fdb-178">The Part Assembly Demo script (shown above) is the script that manages the objects that the user places on the lunar module by the user.</span></span>

<span data-ttu-id="72fdb-179">Il campo oggetto da inserire è la trasformazione selezionata, come illustrato nell'immagine precedente, il serbatoio dello zaino o del carburante associato all'oggetto a cui si connette.</span><span class="sxs-lookup"><span data-stu-id="72fdb-179">The Object To Place field is the transform that is selected, as shown in the image above, the backpack/fuel tank associated with the object that it connects to.</span></span>

<span data-ttu-id="72fdb-180">Le impostazioni near distance e distance distance determinano la vicinanza a cui si bloccano le parti o che possono essere rilasciate.</span><span class="sxs-lookup"><span data-stu-id="72fdb-180">The Near Distance and Far Distance settings determine the proximity to which parts snap in place or can be released.</span></span> <span data-ttu-id="72fdb-181">Ad esempio, lo zaino/serbatoio del carburante deve essere di 0,1 unità dal modulo lunare prima di eseguire lo snap-in.</span><span class="sxs-lookup"><span data-stu-id="72fdb-181">For example, the backpack/fuel tank needs to be 0.1 units away from the lunar module before it will snap into place.</span></span> <span data-ttu-id="72fdb-182">L'impostazione distance distance imposta la posizione in cui l'oggetto può essere prima che possa essere scollegato dal modulo lunare.</span><span class="sxs-lookup"><span data-stu-id="72fdb-182">The Far Distance setting sets the location where the object can be before it can detach from the lunar module.</span></span> <span data-ttu-id="72fdb-183">In questo caso, la mano dell'utente deve afferrare l'oggetto equipaggiamento/serbatoio del carburante e spostarlo a 0.2 unità dal modulo lunare per evitare che venga nuovamente ancorato.</span><span class="sxs-lookup"><span data-stu-id="72fdb-183">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="72fdb-184">L'oggetto descrizione comando è l'etichetta descrizione comando nella scena.</span><span class="sxs-lookup"><span data-stu-id="72fdb-184">The Tool Tip Object is the tool tip label in the scene.</span></span> <span data-ttu-id="72fdb-185">Quando gli oggetti vengono bloccati sul posto, l'etichetta è disabilitata.</span><span class="sxs-lookup"><span data-stu-id="72fdb-185">When the objects are snapped in place, the label is disabled.</span></span>

<span data-ttu-id="72fdb-186">L'origine audio viene afferrata automaticamente.</span><span class="sxs-lookup"><span data-stu-id="72fdb-186">The Audio Source is automatically grabbed.</span></span>

### <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="72fdb-187">Configurazione del pulsante degli hint di selezione host</span><span class="sxs-lookup"><span data-stu-id="72fdb-187">Configuring the Placement Hints button</span></span>

<span data-ttu-id="72fdb-188">Nella [lezione 2](mrlearning-base-ch2.md)si è appreso come posizionare e configurare i pulsanti per eseguire operazioni quali la modifica del colore di un elemento o la riproduzione di un suono quando viene effettuato il push.</span><span class="sxs-lookup"><span data-stu-id="72fdb-188">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when pushed.</span></span> <span data-ttu-id="72fdb-189">Useremo questi stessi principi per configurare i pulsanti in modo da attivare o disattivare i suggerimenti di posizionamento.</span><span class="sxs-lookup"><span data-stu-id="72fdb-189">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span>

<span data-ttu-id="72fdb-190">Lo scopo è quello di configurare il pulsante in modo che ogni volta che l'utente preme il pulsante dell'hint di selezione host, la visibilità degli hint di posizionamento translucidi.</span><span class="sxs-lookup"><span data-stu-id="72fdb-190">The goal is to configure our button so that every time the user presses the Placement hint button, it toggles the visibility of the translucent placement hints.</span></span>

1. <span data-ttu-id="72fdb-191">Spostare il modulo Lunar nello slot di runtime vuoto solo nel pannello Inspector mentre l'oggetto hint di posizionamento è selezionato nella gerarchia di base della scena.</span><span class="sxs-lookup"><span data-stu-id="72fdb-191">Move the lunar module to the empty Runtime Only slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span>

    ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG)

2. <span data-ttu-id="72fdb-193">Fare clic sull'elenco a discesa nessuna funzione.</span><span class="sxs-lookup"><span data-stu-id="72fdb-193">Click the No Function dropdown list.</span></span> <span data-ttu-id="72fdb-194">Passare a TogglePlacementHints e selezionare ToggleGameObjects () in questo menu.</span><span class="sxs-lookup"><span data-stu-id="72fdb-194">Go down to TogglePlacementHints and select ToggleGameObjects () under that menu.</span></span> <span data-ttu-id="72fdb-195">ToggleGameObjects () consente di attivare e disattivare gli hint di selezione host in modo che siano visibili o invisibili ogni volta che viene premuto il pulsante.</span><span class="sxs-lookup"><span data-stu-id="72fdb-195">ToggleGameObjects() toggles the placement hints on and off so that they are visible or invisible each time the button is pressed.</span></span>

    ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a><span data-ttu-id="72fdb-197">Configurazione del pulsante Reimposta</span><span class="sxs-lookup"><span data-stu-id="72fdb-197">Configuring the Reset button</span></span>

<span data-ttu-id="72fdb-198">Si verificheranno situazioni in cui l'utente commette un errore, genera accidentalmente l'oggetto o semplicemente vuole reimpostare l'esperienza.</span><span class="sxs-lookup"><span data-stu-id="72fdb-198">There will be situations where the user makes a mistake, accidentally throws the object away or just wants to reset the experience.</span></span> <span data-ttu-id="72fdb-199">Il pulsante Reimposta consente di riavviare l'esperienza.</span><span class="sxs-lookup"><span data-stu-id="72fdb-199">The Reset button adds the ability to restart the experience.</span></span>

1. <span data-ttu-id="72fdb-200">Selezionare il pulsante Reimposta.</span><span class="sxs-lookup"><span data-stu-id="72fdb-200">Select the Reset button.</span></span> <span data-ttu-id="72fdb-201">Nella scena di base è denominato ResetRoundButton.</span><span class="sxs-lookup"><span data-stu-id="72fdb-201">In the base scene, it’s named ResetRoundButton.</span></span>

2. <span data-ttu-id="72fdb-202">Trascinare il modulo Lunar dalla gerarchia di base della scena nello slot vuoto sotto il pulsante premuto nel pannello Inspector.</span><span class="sxs-lookup"><span data-stu-id="72fdb-202">Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed on the inspector panel.</span></span>

    ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

3. <span data-ttu-id="72fdb-204">Selezionare il menu a discesa nessuna funzione e passare il mouse su LaunchLunarModule, quindi selezionare resetModule ().</span><span class="sxs-lookup"><span data-stu-id="72fdb-204">Select the No Function dropdown menu and hover over LaunchLunarModule, then select resetModule ().</span></span>

    ![Immagine lezione 6 capitolo 4 passaggio 3](images/Lesson6_Chapter4_step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="72fdb-206">Si noti che per impostazione predefinita, GameObject. BroadcastMessage è configurato per ResetPlacement.</span><span class="sxs-lookup"><span data-stu-id="72fdb-206">Notice that by default, the GameObject.BroadcastMessage is configured to ResetPlacement.</span></span> <span data-ttu-id="72fdb-207">Viene trasmesso un messaggio denominato ResetPlacement per ogni oggetto figlio della RocketLauncher_Tutorial.</span><span class="sxs-lookup"><span data-stu-id="72fdb-207">This broadcasts a message named ResetPlacement for every child object of the RocketLauncher_Tutorial.</span></span> <span data-ttu-id="72fdb-208">Qualsiasi oggetto con un metodo per ResetPlacement () risponde a tale messaggio reimpostando la relativa posizione.</span><span class="sxs-lookup"><span data-stu-id="72fdb-208">Any object that has a method for ResetPlacement() responds to that message by resetting it's position.</span></span>

### <a name="configuring-the-launch-button"></a><span data-ttu-id="72fdb-209">Configurazione del pulsante Launch</span><span class="sxs-lookup"><span data-stu-id="72fdb-209">Configuring the Launch button</span></span>

<span data-ttu-id="72fdb-210">Questa sezione illustra come configurare il pulsante Launch (avvio), che consente all'utente di premere il pulsante e avviare il modulo Lunar nello spazio.</span><span class="sxs-lookup"><span data-stu-id="72fdb-210">This section explains how to configure the Launch button, which permits the user to press the button and launch the lunar module into space.</span></span>

1. <span data-ttu-id="72fdb-211">Selezionare il pulsante Launch (Avvia).</span><span class="sxs-lookup"><span data-stu-id="72fdb-211">Select the Launch button.</span></span> <span data-ttu-id="72fdb-212">Nella scena di base viene chiamato LaunchRoundButton.</span><span class="sxs-lookup"><span data-stu-id="72fdb-212">In the base scene, it’s called LaunchRoundButton.</span></span> <span data-ttu-id="72fdb-213">Trascinare il modulo Lunar nello slot vuoto sotto touch end nel pannello Inspector.</span><span class="sxs-lookup"><span data-stu-id="72fdb-213">Drag the lunar module to the empty slot under Touch End in the Inspector panel.</span></span>

    ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG)

2. <span data-ttu-id="72fdb-215">Selezionare il menu a discesa nessuna funzione e passare il puntatore del mouse su LaunchLunarModule e selezionare StopThruster ().</span><span class="sxs-lookup"><span data-stu-id="72fdb-215">Select the No Function dropdown menu and hover over LaunchLunarModule, and select StopThruster ().</span></span> <span data-ttu-id="72fdb-216">Consente di controllare la quantità di spinta che l'utente desidera assegnare al modulo lunare.</span><span class="sxs-lookup"><span data-stu-id="72fdb-216">This controls how much thrust the user wants to give to the lunar module.</span></span>

    ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)

3. <span data-ttu-id="72fdb-218">Trascinare il modulo Lunar dalla gerarchia di base della scena nello slot vuoto in Button premuto nel pannello Inspector.</span><span class="sxs-lookup"><span data-stu-id="72fdb-218">Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed in the inspector panel.</span></span>

4. <span data-ttu-id="72fdb-219">Fare clic sul menu a discesa nessuna funzione e quindi su LaunchLunarModule e selezionare StartThruster ().</span><span class="sxs-lookup"><span data-stu-id="72fdb-219">Click the No function dropdown menu and then on LaunchLunarModule and select StartThruster ().</span></span>

    ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)

5. <span data-ttu-id="72fdb-221">Aggiungere musica al modulo Lunar in modo che la musica riproduca quando il razzo decolla.</span><span class="sxs-lookup"><span data-stu-id="72fdb-221">Add music to the lunar module so that music plays when the rocket takes off.</span></span> <span data-ttu-id="72fdb-222">A tale scopo, trascinare il modulo Lunar sul successivo slot vuoto sotto il pulsante premuto ().</span><span class="sxs-lookup"><span data-stu-id="72fdb-222">To do this, drag the lunar module to the next empty slot under Button Pressed().</span></span>

6. <span data-ttu-id="72fdb-223">Selezionare il menu a discesa nessuna funzione, passare il mouse su AudioSource e selezionare PlayOneShot (AudioClip).</span><span class="sxs-lookup"><span data-stu-id="72fdb-223">Select the No Function dropdown menu, hover over AudioSource and select PlayOneShot (AudioClip).</span></span> <span data-ttu-id="72fdb-224">Esplora la varietà di suoni inclusi in MRTK.</span><span class="sxs-lookup"><span data-stu-id="72fdb-224">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="72fdb-225">In questo esempio si userà "MRTK_Gem".</span><span class="sxs-lookup"><span data-stu-id="72fdb-225">In this example, we'll use "MRTK_Gem."</span></span>

    ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)

### <a name="congratulations"></a><span data-ttu-id="72fdb-227">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="72fdb-227">Congratulations</span></span>

<span data-ttu-id="72fdb-228">Questa applicazione è stata configurata completamente.</span><span class="sxs-lookup"><span data-stu-id="72fdb-228">You have fully configured this application.</span></span> <span data-ttu-id="72fdb-229">A questo punto, quando si preme Play, è possibile assemblare completamente il modulo Lunar, attivare o disabilitare i suggerimenti, avviare il modulo Lunar e reimpostarlo per riavviarlo.</span><span class="sxs-lookup"><span data-stu-id="72fdb-229">Now, when you press play, you can fully assemble the lunar module, toggle hints, launch the lunar module and reset it to start again.</span></span>

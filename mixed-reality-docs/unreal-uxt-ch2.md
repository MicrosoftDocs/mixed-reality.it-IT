---
title: 2. Inizializzazione del progetto e prima applicazione
description: Parte 2 di 6 in una serie di esercitazioni per la creazione di una semplice app di scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione
ms.openlocfilehash: e8f03a87ec6b92e4c62cf3f88f519146254e7387
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330353"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="331d8-104">2. Inizializzazione del progetto e prima applicazione</span><span class="sxs-lookup"><span data-stu-id="331d8-104">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="331d8-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="331d8-105">Overview</span></span>

<span data-ttu-id="331d8-106">In questa prima esercitazione inizierai a creare una nuova applicazione Unreal per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="331d8-106">In this first tutorial, you'll get started with a new Unreal application for HoloLens 2.</span></span> <span data-ttu-id="331d8-107">Eseguirai varie operazioni, come aggiungere il plug-in HoloLens, creare e illuminare un livello e popolarlo con una scacchiera e un pezzo degli scacchi.</span><span class="sxs-lookup"><span data-stu-id="331d8-107">This is going to include adding the HoloLens plugin, creating and lighting a level, and populating it with a game board and chess piece.</span></span> <span data-ttu-id="331d8-108">Non dovrai modellare nulla da zero perché userai asset predefiniti per il pezzo degli scacchi 3D e i materiali degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="331d8-108">You'll be using pre-made assets for the 3D chess piece and object materials, so don't worry about modeling anything from scratch.</span></span> <span data-ttu-id="331d8-109">Al termine di questa esercitazione avrai un'area di disegno vuota pronta da configurare per la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="331d8-109">By the end of this tutorial you'll have a blank canvas that's ready for mixed reality.</span></span>

<span data-ttu-id="331d8-110">Prima di proseguire, assicurarsi di disporre di tutti i prerequisiti indicati nella [Guida introduttiva](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1).</span><span class="sxs-lookup"><span data-stu-id="331d8-110">Before continuing, make sure you have all the prerequisite from the [Getting Started](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1) page.</span></span>

## <a name="objectives"></a><span data-ttu-id="331d8-111">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="331d8-111">Objectives</span></span>
* <span data-ttu-id="331d8-112">Configurazione di un progetto Unreal per lo sviluppo per HoloLens</span><span class="sxs-lookup"><span data-stu-id="331d8-112">Configuring an Unreal projet for HoloLens development</span></span>
* <span data-ttu-id="331d8-113">Importazione di asset e configurazione di una scena</span><span class="sxs-lookup"><span data-stu-id="331d8-113">Importing assets and setting up a scene</span></span>
* <span data-ttu-id="331d8-114">Creazione di attori ed eventi a livello di script con progetti</span><span class="sxs-lookup"><span data-stu-id="331d8-114">Creating Actors and script-level events with blueprints</span></span>

## <a name="creating-a-new-unreal-project"></a><span data-ttu-id="331d8-115">Creazione di un nuovo progetto Unreal</span><span class="sxs-lookup"><span data-stu-id="331d8-115">Creating a new Unreal project</span></span>
<span data-ttu-id="331d8-116">Prima di tutto, è necessario un progetto su cui lavorare.</span><span class="sxs-lookup"><span data-stu-id="331d8-116">The first thing you need is a project to work with.</span></span>

1. <span data-ttu-id="331d8-117">Avvia Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="331d8-117">Launch Unreal Engine</span></span>

2. <span data-ttu-id="331d8-118">Seleziona **Games** (Giochi) in **New Project Categories** (Categorie nuovo progetto) e fai clic su **Next** (Avanti).</span><span class="sxs-lookup"><span data-stu-id="331d8-118">Select **Games** in **New Project Categories** and click **Next**.</span></span> 

![Selezionare il modello di progetto Games (Giochi)](images/unreal-uxt/2-gamestemplate.png)

3. <span data-ttu-id="331d8-120">Seleziona il modello **Blank** (Vuoto) e fai clic su **Next** (Avanti).</span><span class="sxs-lookup"><span data-stu-id="331d8-120">Select the **Blank** Template and click **Next**.</span></span> 

![Selezionare il modello vuoto](images/unreal-uxt/2-template.PNG)

4. <span data-ttu-id="331d8-122">Imposta **C++** , **Scalable 3D or 2D, Mobile/Tablet** (3D o 2D scalabile, Cellulare/Tablet) e **No Starter Content** (Nessun contenuto iniziale) in **Project Settings** (Impostazioni progetto).</span><span class="sxs-lookup"><span data-stu-id="331d8-122">Set **C++**, **Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content** as your **Project Settings**.</span></span> 
    * <span data-ttu-id="331d8-123">Scegli una posizione di salvataggio e fai clic su **Create Project** (Crea progetto).</span><span class="sxs-lookup"><span data-stu-id="331d8-123">Choose a save location and click **Create Project**.</span></span> 

![Impostazioni iniziali del progetto](images/unreal-uxt/2-project-settings.PNG)

<span data-ttu-id="331d8-125">Il progetto dovrebbe aprirsi automaticamente nell'editor Unreal e a quel punto puoi passare alla sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="331d8-125">The project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="331d8-126">Abilitazione dei plug-in necessari</span><span class="sxs-lookup"><span data-stu-id="331d8-126">Enabling required plugins</span></span>
<span data-ttu-id="331d8-127">Prima di iniziare ad aggiungere oggetti alla scena, è necessario abilitare due plug-in.</span><span class="sxs-lookup"><span data-stu-id="331d8-127">Before you start adding objects to the scene you'll need to enable two plugins.</span></span>

1. <span data-ttu-id="331d8-128">Apri **Edit > Plugins** (Modifica > Plug-in) e seleziona **Augmented Reality** (Realtà aumentata) nell'elenco di opzioni predefinite.</span><span class="sxs-lookup"><span data-stu-id="331d8-128">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="331d8-129">Scorri verso il basso fino a **HoloLens** e seleziona **Enabled** (Abilitato).</span><span class="sxs-lookup"><span data-stu-id="331d8-129">Scroll down to **HoloLens** and check **Enabled**.</span></span> 

![Abilitazione dei plug-in HoloLens](images/unreal-uxt/2-plugins.PNG)

2. <span data-ttu-id="331d8-131">Seleziona **Virtual Reality** (Realtà virtuale) nell'elenco di opzioni predefinite.</span><span class="sxs-lookup"><span data-stu-id="331d8-131">Select **Virtual Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="331d8-132">Scorri verso il basso fino a **Microsoft Windows Mixed Reality**, seleziona **Enabled** (Abilitato) e riavvia l'editor.</span><span class="sxs-lookup"><span data-stu-id="331d8-132">Scroll down to **Microsoft Windows Mixed Reality**., check **Enabled**, and restart your editor.</span></span> 

![Abilitazione del plug-in Windows Mixed Reality](images/unreal-uxt/2-virtual-reality-plugin.PNG)

> [!NOTE]
> <span data-ttu-id="331d8-134">Per lo sviluppo di HoloLens 2 sono necessari entrambi i plug-in.</span><span class="sxs-lookup"><span data-stu-id="331d8-134">Both plugins are required for HoloLens 2 development.</span></span>

<span data-ttu-id="331d8-135">Terminata questa configurazione, puoi iniziare a creare altri livelli.</span><span class="sxs-lookup"><span data-stu-id="331d8-135">With that done you're empty level is ready for company.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="331d8-136">Creazione di un livello</span><span class="sxs-lookup"><span data-stu-id="331d8-136">Creating a level</span></span>
<span data-ttu-id="331d8-137">L'attività successiva consiste nel creare una semplice configurazione di gioco con un punto iniziale e un cubo per riferimento e scala.</span><span class="sxs-lookup"><span data-stu-id="331d8-137">Your next task is to create a simple player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="331d8-138">Seleziona **File > New Level** (File > Nuovo livello) e scegli **Empty Level** (Livello vuoto).</span><span class="sxs-lookup"><span data-stu-id="331d8-138">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="331d8-139">In questa fase, la scena predefinita nel riquadro di visualizzazione dovrebbe essere vuota.</span><span class="sxs-lookup"><span data-stu-id="331d8-139">The default scene in the viewport should now be empty.</span></span>

2. <span data-ttu-id="331d8-140">Seleziona **Basic** (Base) nella scheda **Modes** (Modalità) e trascina **PlayerStart** nella scena.</span><span class="sxs-lookup"><span data-stu-id="331d8-140">Select **Basic** from the **Modes** tab and drag **PlayerStart** into the scene.</span></span> 
    * <span data-ttu-id="331d8-141">Imposta **Location** (Posizione) su **X = 0**, **Y = 0** e **Z = 0** nella scheda **Details** (Dettagli). L'utente viene posizionato al centro della scena all'avvio dell'app.</span><span class="sxs-lookup"><span data-stu-id="331d8-141">Set **Location** to **X = 0**, **Y = 0**, and **Z = 0** in the **Details** tab. This sets the user at the center of the scene when the app starts up.</span></span>

![Riquadro di visualizzazione con PlayerStart](images/unreal-uxt/2-playerstart.PNG)

3. <span data-ttu-id="331d8-143">Trascina un oggetto **Cube** (Cubo) dalla scheda **Basic** (Base) nella scena.</span><span class="sxs-lookup"><span data-stu-id="331d8-143">Drag a **Cube** from the **Basic** tab into the scene.</span></span> 
    * <span data-ttu-id="331d8-144">Imposta **Location** (Posizione) su **X = 50**, **Y = 0** e **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="331d8-144">Set **Location** to **X = 50**, **Y = 0**, and **Z = 0**.</span></span> <span data-ttu-id="331d8-145">Il cubo viene posizionato a 50 cm di distanza dal giocatore al momento dell'avvio.</span><span class="sxs-lookup"><span data-stu-id="331d8-145">This positions the cube 50 cm away from the player at start time.</span></span> 
    * <span data-ttu-id="331d8-146">Imposta **Scale** (Scala) su **X = 0.2**, **Y = 0.2** e **Z = 0.2** per ridurre le dimensioni del cubo.</span><span class="sxs-lookup"><span data-stu-id="331d8-146">Change **Scale** to **X = 0.2**, **Y = 0.2**, and **Z = 0.2** to shrink the cube down.</span></span> 

<span data-ttu-id="331d8-147">Il cubo non sarà visibile finché non aggiungerai una luce alla scena, che è l'ultima attività da eseguire prima di testare la scena.</span><span class="sxs-lookup"><span data-stu-id="331d8-147">You won’t be able to see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="331d8-148">Passa alla scheda **Lights** (Luci) nel pannello **Modes** (Modalità) e trascina un oggetto **Directional Light** (Luce direzionale) nella scena.</span><span class="sxs-lookup"><span data-stu-id="331d8-148">Switch to the **Lights** tab in the **Modes** panel and drag a **Directional Light** into the scene.</span></span> <span data-ttu-id="331d8-149">Posiziona la luce al di sopra di **PlayerStart** perché sia visibile.</span><span class="sxs-lookup"><span data-stu-id="331d8-149">Position the light above **PlayerStart** so you can see it.</span></span>

![Riquadro di visualizzazione con aggiunta di luce](images/unreal-uxt/2-light.PNG)

5. <span data-ttu-id="331d8-151">Passa a **File > Save Current** (File > Salva corrente), assegna il nome **Main** (Principale) al livello e fai clic su **Save** (Salva).</span><span class="sxs-lookup"><span data-stu-id="331d8-151">Go to **File > Save Current**, name your level **Main**, and click **Save**.</span></span> 

<span data-ttu-id="331d8-152">Una volta impostata la scena, seleziona **Play** (Riproduci) sulla barra degli strumenti per vedere il cubo in azione.</span><span class="sxs-lookup"><span data-stu-id="331d8-152">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="331d8-153">Quando avrai terminato di ammirare il tuo lavoro, premi **ESC** per arrestare l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="331d8-153">When you're finished admiring your work, press **Esc** to stop the application.</span></span>

![Un cubo nel riquadro di visualizzazione](images/unreal-uxt/2-cube.PNG)

<span data-ttu-id="331d8-155">Ora che la scena è configurata, puoi iniziare ad aggiungere la scacchiera e il pezzo per completare l'ambiente dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="331d8-155">Now that the scene is setup, you can start adding in the chess board and piece to round out the application environment.</span></span>

## <a name="importing-assets"></a><span data-ttu-id="331d8-156">Importazione di asset</span><span class="sxs-lookup"><span data-stu-id="331d8-156">Importing assets</span></span>
<span data-ttu-id="331d8-157">Al momento la scena è un po' spoglia, ma puoi arricchirla importando asset predefiniti nel progetto.</span><span class="sxs-lookup"><span data-stu-id="331d8-157">The scene is looking a bit empty at the moment, but you'll fix that by importing the ready-made assets into the project.</span></span>

1. <span data-ttu-id="331d8-158">Scarica e decomprimi la cartella di asset [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z).</span><span class="sxs-lookup"><span data-stu-id="331d8-158">Download and unzip the [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) assets folder.</span></span>

2. <span data-ttu-id="331d8-159">Fai clic su **Add New > New Folder** (Aggiungi nuovo > Nuova cartella) in **Content Browser** (Browser contenuto) e assegna il nome **ChessAssets** alla cartella.</span><span class="sxs-lookup"><span data-stu-id="331d8-159">Click **Add New > New Folder** from the **Content Browser** and name it **ChessAssets**.</span></span> 
    * <span data-ttu-id="331d8-160">Fai doppio clic sulla nuova cartella, in cui importerai gli asset 3D.</span><span class="sxs-lookup"><span data-stu-id="331d8-160">Double-click the new folder - this is where you'll import the 3D assets.</span></span>

![Visualizzare o nascondere il pannello delle origini](images/unreal-uxt/2-showhidesources.PNG)

3. <span data-ttu-id="331d8-162">Fai clic su **Import** (Importa) in **Content Browser** (Browser contenuto), seleziona tutti gli elementi nella cartella di asset decompressa e scegli **Open** (Apri).</span><span class="sxs-lookup"><span data-stu-id="331d8-162">Click **Import** from the **Content Browser**, select all the items in the unzipped assets folder and click **Open**.</span></span> 
    * <span data-ttu-id="331d8-163">Questa cartella contiene le mesh degli oggetti 3D per la scacchiera e i pezzi in formato FBX e le mappe di texture in formato TGA che userai per i materiali.</span><span class="sxs-lookup"><span data-stu-id="331d8-163">This folder contains the 3D object meshes for the chess board and pieces in FBX format and texture maps in TGA format that you'll use to for materials.</span></span>  

4. <span data-ttu-id="331d8-164">Quando viene visualizzata la finestra FBX Import Options (Opzioni di importazione FBX), espandi la sezione **Material** (Materiale) e modifica **Material Import Method** (Metodo importazione materiale) in **Do Not Create Material** (Non creare materiale).</span><span class="sxs-lookup"><span data-stu-id="331d8-164">When the FBX Import Options window pops up, expand the **Material** section and change **Material Import Method** to **Do Not Create Material**.</span></span>
    * <span data-ttu-id="331d8-165">Fai clic su **Import All** (Importa tutto).</span><span class="sxs-lookup"><span data-stu-id="331d8-165">Click **Import All**.</span></span>

![Opzioni importazione FBX](images/unreal-uxt/2-nocreatemat.PNG)

<span data-ttu-id="331d8-167">Non serve fare altro per gli asset.</span><span class="sxs-lookup"><span data-stu-id="331d8-167">That's all you need to do for the assets.</span></span> <span data-ttu-id="331d8-168">Il prossimo set di attività consiste nel creare i blocchi predefiniti dell'applicazione con i progetti.</span><span class="sxs-lookup"><span data-stu-id="331d8-168">Your next set of tasks is to create the building blocks of the application with blueprints.</span></span>

## <a name="adding-blueprints"></a><span data-ttu-id="331d8-169">Aggiunta di progetti</span><span class="sxs-lookup"><span data-stu-id="331d8-169">Adding blueprints</span></span>

1. <span data-ttu-id="331d8-170">Fai clic su **Add New > New Folder** (Aggiungi nuovo > Nuova cartella) in **Content Browser** (Browser contenuto) e assegna il nome **Content Browser** (Browser contenuto) alla cartella.</span><span class="sxs-lookup"><span data-stu-id="331d8-170">Click **Add New > New Folder** in the **Content Browser** and name it **Content Browser**.</span></span> 

> [!NOTE]
> <span data-ttu-id="331d8-171">I [progetti](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html) sono asset speciali che forniscono un'interfaccia basata su nodi per la creazione di nuovi tipi di attori ed eventi a livello di script.</span><span class="sxs-lookup"><span data-stu-id="331d8-171">If you're new to [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), they're special assets that provide a node-based interface for creating new types of Actors and script level events.</span></span> 

2. <span data-ttu-id="331d8-172">Fai doppio clic nella cartella **Blueprints** (Progetti), quindi fai clic con il pulsante destro del mouse e scegli **Blueprint Class** (Classe progetto).</span><span class="sxs-lookup"><span data-stu-id="331d8-172">Double-click into the **Blueprints** folder, then right-click and select **Blueprint Class**.</span></span>         
    * <span data-ttu-id="331d8-173">Seleziona **Actor** (Attore) e assegna al nuovo progetto il nome **Board** (Tavola).</span><span class="sxs-lookup"><span data-stu-id="331d8-173">Select **Actor** and name the blueprint **Board**.</span></span> 

![Selezionare una classe padre per il progetto](images/unreal-uxt/2-bpparent.PNG)

<span data-ttu-id="331d8-175">Il nuovo progetto **Board** (Tavola) verrà incluso nella cartella **Blueprints** (Progetti) mostrata nello screenshot seguente.</span><span class="sxs-lookup"><span data-stu-id="331d8-175">The new **Board** blueprint now shows up in the **Blueprints** folder as seen in the following screenshot.</span></span> 

![Nuovo progetto Board (Tavola)](images/unreal-uxt/2-bpboard.PNG)

<span data-ttu-id="331d8-177">È tutto pronto per iniziare ad aggiungere materiali agli oggetti creati.</span><span class="sxs-lookup"><span data-stu-id="331d8-177">You're all set to start adding materials to the created objects.</span></span>

## <a name="working-with-materials"></a><span data-ttu-id="331d8-178">Uso dei materiali</span><span class="sxs-lookup"><span data-stu-id="331d8-178">Working with materials</span></span>
<span data-ttu-id="331d8-179">Gli oggetti che hai creato sono grigi per impostazione predefinita e questo non li rende particolarmente gradevoli dal punto di vista estetico.</span><span class="sxs-lookup"><span data-stu-id="331d8-179">The objects you've created are default grey, which isn't much fun to look at.</span></span> <span data-ttu-id="331d8-180">L'ultima serie di attività di questa esercitazione consiste appunto nell'aggiungere materiali e mesh agli oggetti.</span><span class="sxs-lookup"><span data-stu-id="331d8-180">Adding materials and meshes to your objects is the last set of tasks in this tutorial.</span></span>

1. <span data-ttu-id="331d8-181">Fai doppio clic su **Board** (Tavola) per aprire l'editor dei progetti.</span><span class="sxs-lookup"><span data-stu-id="331d8-181">Double-click **Board** to open the blueprint editor.</span></span> 

2. <span data-ttu-id="331d8-182">Fai clic su **Add Component > Scene** (Aggiungi componente > Scena) nel pannello **Components** (Componenti) e assegna il nome **Root** (Radice) alla scena.</span><span class="sxs-lookup"><span data-stu-id="331d8-182">Click **Add Component > Scene** from the **Components** panel and name it **Root**.</span></span> <span data-ttu-id="331d8-183">Nota che **Root** (Radice) viene visualizzato come elemento figlio di **DefaultSceneRoot** nello screenshot seguente:</span><span class="sxs-lookup"><span data-stu-id="331d8-183">Notice that **Root** shows up as a child of **DefaultSceneRoot** in the screenshot below:</span></span>

![Sostituzione della radice](images/unreal-uxt/2-root-blueprint.PNG)


3. <span data-ttu-id="331d8-185">Trascina **Root** (Radice) su **DefaultSceneRoot** per sostituire la radice ed eliminare la sfera nel viewport.</span><span class="sxs-lookup"><span data-stu-id="331d8-185">Click-and-drag **Root** onto **DefaultSceneRoot** to replace it and get rid of the sphere in the viewport.</span></span> 

![Sostituzione della radice](images/unreal-uxt/2-root.PNG)


4. <span data-ttu-id="331d8-187">Fai clic su **Add Component > Static Mesh** (Aggiungi componente > Mesh statica) nel pannello **Components** (Componenti) e assegna il nome **SM_Board** (MS_Tavola) alla mesh statica.</span><span class="sxs-lookup"><span data-stu-id="331d8-187">Click **Add Component > Static Mesh** from the **Components** panel and name it **SM_Board**.</span></span> <span data-ttu-id="331d8-188">Verrà visualizzata come oggetto figlio in **Root** (Radice).</span><span class="sxs-lookup"><span data-stu-id="331d8-188">It will appear as a child object under **Root**.</span></span>

![Aggiunta di una mesh statica](images/unreal-uxt/2-sm-board.PNG)

4. <span data-ttu-id="331d8-190">Fai clic su **SM_Board** (MS_Tavola), scorri verso il basso fino alla sezione **Static Mesh** (Mesh statica) del pannello **Details** (Dettagli) e quindi seleziona **ChessBoard** (Scacchiera) nell'elenco a discesa.</span><span class="sxs-lookup"><span data-stu-id="331d8-190">Click **SM_Board**, scroll down to the **Static Mesh** section of the **Details** panel, and select **ChessBoard** from the dropdown.</span></span> 

![Mesh Tavola nel riquadro di visualizzazione](images/unreal-uxt/2-sm-board-view.PNG)

5.  <span data-ttu-id="331d8-192">Sempre nel pannello **Details** (Dettagli) espandi la sezione **Materials** (Materiali) e fai clic su **Create New Asset > Material** (Crea nuovo asset > Materiale) nell'elenco a discesa.</span><span class="sxs-lookup"><span data-stu-id="331d8-192">Still in the **Details** panel, expand the **Materials** section and click **Create New Asset > Material** from the dropdown.</span></span> 
    * <span data-ttu-id="331d8-193">Assegna a questo materiale il nome **M_ChessBoard** (M_Scacchiera) e salvalo nella cartella **ChessAssets**.</span><span class="sxs-lookup"><span data-stu-id="331d8-193">Name the material **M_ChessBoard** and save it to the **ChessAssets** folder.</span></span> 

![Creare un nuovo materiale](images/unreal-uxt/2-newmat.PNG)

6.  <span data-ttu-id="331d8-195">Fai doppio clic sull'immagine del materiale **M_ChessBoard** (M_Scacchiera) per aprire l'editor dei materiali.</span><span class="sxs-lookup"><span data-stu-id="331d8-195">Double-click the **M_ChessBoard** material imaged to open the Material Editor.</span></span> 

![Aprire l'editor dei materiali](images/unreal-uxt/2-material-editor.PNG)

7. <span data-ttu-id="331d8-197">Nell'editor dei materiali fai clic con il pulsante destro del mouse e cerca **Texture Sample** (Esempio di texture).</span><span class="sxs-lookup"><span data-stu-id="331d8-197">In the Material Editor, right-click and search for **Texture Sample**.</span></span> 
    * <span data-ttu-id="331d8-198">Espandi la sezione **Material Expression Texture Base** (Espressione materiale - Base texture) nel pannello **Details** (Dettagli) e imposta **Texture** su **ChessBoard_Albedo** (Scacchiera_Albedo).</span><span class="sxs-lookup"><span data-stu-id="331d8-198">Expand the **Material Expression Texture Base** section in the **Details** panel and set **Texture** to **ChessBoard_Albedo**.</span></span> 
    * <span data-ttu-id="331d8-199">Trascina il segnaposto di output **RGB** sul segnaposto Base Color (Colore di base) di **M_ChessBoard** (M_Scacchiera).</span><span class="sxs-lookup"><span data-stu-id="331d8-199">Drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![Impostare il colore di base](images/unreal-uxt/2-boardalbedomat.PNG)

8.  <span data-ttu-id="331d8-201">Ripeti altre quattro volte il passaggio precedente per creare altri quattro nodi **Texture Sample** (Esempio di texture) con le impostazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="331d8-201">Repeat the previous step four more times to create four more **Texture Sample** nodes with the following settings:</span></span>
    * <span data-ttu-id="331d8-202">Imposta **Texture** su **ChessBoard_AO** (Scacchiera_OA) e collega **RGB** al segnaposto **Ambient Occlusion** (Occlusione ambiente).</span><span class="sxs-lookup"><span data-stu-id="331d8-202">Set **Texture** to **ChessBoard_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="331d8-203">Imposta **Texture** su **ChessBoard_Metal**(Scacchiera_Metallo) e collega **RGB** al segnaposto **Metallic** (Metallico).</span><span class="sxs-lookup"><span data-stu-id="331d8-203">Set **Texture** to **ChessBoard_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="331d8-204">Imposta **Texture** su **ChessBoard_Normal** (Scacchiera_Normale) e collega **RGB** al segnaposto **Normal** (Normale).</span><span class="sxs-lookup"><span data-stu-id="331d8-204">Set **Texture** to **ChessBoard_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="331d8-205">Imposta **Texture** su **ChessBoard_Rough**(Scacchiera_Ruvido) e collega **RGB** al segnaposto **Roughness** (Ruvidezza).</span><span class="sxs-lookup"><span data-stu-id="331d8-205">Set **Texture** to **ChessBoard_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="331d8-206">Fai clic su **Save** (Salva).</span><span class="sxs-lookup"><span data-stu-id="331d8-206">Click **Save**.</span></span> 

![Associare le texture rimanenti](images/unreal-uxt/2-boardmat.PNG)

<span data-ttu-id="331d8-208">Prima di continuare, verifica che la configurazione del materiale corrisponda allo screenshot riportato sopra.</span><span class="sxs-lookup"><span data-stu-id="331d8-208">Make sure the your material setup looks like the above screenshot before continuing.</span></span>

## <a name="populating-the-scene"></a><span data-ttu-id="331d8-209">Popolamento della scena</span><span class="sxs-lookup"><span data-stu-id="331d8-209">Populating the scene</span></span>
<span data-ttu-id="331d8-210">Se torni al progetto **Board** (Tavola), noterai che il materiale appena creato è stato applicato.</span><span class="sxs-lookup"><span data-stu-id="331d8-210">If you go back to the **Board** blueprint, you'll see that the material you just created has been applied.</span></span> <span data-ttu-id="331d8-211">A questo punto devi solo configurare la scena.</span><span class="sxs-lookup"><span data-stu-id="331d8-211">All that's left is setting up the scene!</span></span> <span data-ttu-id="331d8-212">Prima di tutto, modifica le proprietà seguenti per assicurarti che la scacchiera sia di dimensioni ragionevoli e disposta nella corretta angolazione quando viene inserita nella scena:</span><span class="sxs-lookup"><span data-stu-id="331d8-212">First, change the following properties to make sure the board is a reasonable size and angled correctly when it's placed in the scene:</span></span>
1.  <span data-ttu-id="331d8-213">Imposta **Scale** (Scala) su **(0.05, 0.05, 0.05)** e **Z Rotation** (Rotazione Z) su **90**.</span><span class="sxs-lookup"><span data-stu-id="331d8-213">Set **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span> 
    * <span data-ttu-id="331d8-214">Fai clic su **Compile** (Compila) sulla barra degli strumenti in alto, quindi su **Save** (Salva) e torna alla finestra principale.</span><span class="sxs-lookup"><span data-stu-id="331d8-214">Click **Compile** in the top toolbar, then **Save** and return to the Main window.</span></span> 

![Scacchiera con materiale applicato](images/unreal-uxt/2-chessboard.PNG)

2.  <span data-ttu-id="331d8-216">Fai clic con il pulsante destro del mouse su **Cube > Edit > Delete** (Cubo > Modifica > Elimina) e trascina **Board** (Tavola) da **Content Browser** (Browser contenuto) nel viewport.</span><span class="sxs-lookup"><span data-stu-id="331d8-216">Right-click **Cube > Edit > Delete** and drag **Board** from the **Content Browser** into the viewport.</span></span> 
    * <span data-ttu-id="331d8-217">Imposta **Location** (Posizione) su **X = 80**, **Y = 0** e **Z = 20**.</span><span class="sxs-lookup"><span data-stu-id="331d8-217">Set **Location** to **X = 80**, **Y = 0**, and **Z = -20**.</span></span> 

3.  <span data-ttu-id="331d8-218">Fai clic sul pulsante **Play** per visualizzare la nuova tavola nel livello.</span><span class="sxs-lookup"><span data-stu-id="331d8-218">Click the **Play** button to view your new board in the level.</span></span> <span data-ttu-id="331d8-219">Premi **ESC** per tornare all'editor.</span><span class="sxs-lookup"><span data-stu-id="331d8-219">Press **Esc** to return to the editor.</span></span> 

<span data-ttu-id="331d8-220">A questo punto creerai un pezzo degli scacchi seguendo la stessa procedura usata per la scacchiera:</span><span class="sxs-lookup"><span data-stu-id="331d8-220">Now you'll follow the same steps to create a chess piece as you did with the board:</span></span>

1. <span data-ttu-id="331d8-221">Passa alla cartella **Blueprints** (Progetti), fai clic con il pulsante destro del mouse e scegli **Blueprint Class** (Classe progetto) e **Actor** (Attore).</span><span class="sxs-lookup"><span data-stu-id="331d8-221">Go to the **Blueprints** folder, right-click and select **Blueprint Class** and choose **Actor**.</span></span> <span data-ttu-id="331d8-222">Assegna a questo attore il nome **WhiteKing** (Re bianco).</span><span class="sxs-lookup"><span data-stu-id="331d8-222">Name the actor **WhiteKing**.</span></span>

2. <span data-ttu-id="331d8-223">Fai doppio clic su **WhiteKing** per aprirlo nell'editor progetti, fai clic su **Add Component > Scene** (Aggiungi componente > Scena) e assegna il nome **Root** (Radice) alla scena.</span><span class="sxs-lookup"><span data-stu-id="331d8-223">Double click **WhiteKing** to open it in the Blueprint Editor, click **Add Component > Scene** and name it **Root**.</span></span> 
    * <span data-ttu-id="331d8-224">Trascina **Root** (Radice) su **DefaultSceneRoot** per sostituirla.</span><span class="sxs-lookup"><span data-stu-id="331d8-224">Drag-and-drop **Root** onto **DefaultSceneRoot** to replace it.</span></span> 

3. <span data-ttu-id="331d8-225">Fai clic su **Add Component > Static Mesh** (Aggiungi componente > Mesh statica) e assegna il nome **SM_King** (MS_Re) alla mesh.</span><span class="sxs-lookup"><span data-stu-id="331d8-225">Click **Add Component > Static Mesh** and name it **SM_King**.</span></span> 
    * <span data-ttu-id="331d8-226">Nel pannello Details (Dettagli) imposta **Static Mesh** (Mesh statica) su **Chess_King** (Scacchi_Re) e **Material** (Materiale) su un nuovo materiale denominato **M_ChessWhite** (M_ScacchiBianco).</span><span class="sxs-lookup"><span data-stu-id="331d8-226">Set **Static Mesh** to **Chess_King** and **Material** to a new Material called **M_ChessWhite** in the Details panel.</span></span> 

4. <span data-ttu-id="331d8-227">Apri **M_ChessWhite** (M_ScacchiBianco) nell'editor dei materiali e associa i seguenti nodi **Texture Sample** (Esempio di texture) a quanto segue:</span><span class="sxs-lookup"><span data-stu-id="331d8-227">Open **M_ChessWhite** in the Material editor and hook up the following **Texture Sample** nodes to the following:</span></span>
    * <span data-ttu-id="331d8-228">Imposta **Texture** su **ChessWhite_AO** (ScacchiBianco_OA) e collega **RGB** al segnaposto **Ambient Occlusion** (Occlusione ambiente).</span><span class="sxs-lookup"><span data-stu-id="331d8-228">Set **Texture** to **ChessWhite_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="331d8-229">Imposta **Texture** su **ChessWhite_Metal**(ScacchiBianco_Metallo) e collega **RGB** al segnaposto **Metallic** (Metallico).</span><span class="sxs-lookup"><span data-stu-id="331d8-229">Set **Texture** to **ChessWhite_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="331d8-230">Imposta **Texture** su **ChessWhite_Normal** (ScacchiBianco_Normale) e collega **RGB** al segnaposto **Normal** (Normale).</span><span class="sxs-lookup"><span data-stu-id="331d8-230">Set **Texture** to **ChessWhite_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="331d8-231">Imposta **Texture** su **ChessWhite_Rough**(ScacchiBianco_Ruvido) e collega **RGB** al segnaposto **Roughness** (Ruvidezza).</span><span class="sxs-lookup"><span data-stu-id="331d8-231">Set **Texture** to **ChessWhite_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="331d8-232">Fai clic su **Save** (Salva).</span><span class="sxs-lookup"><span data-stu-id="331d8-232">Click **Save**.</span></span> 

<span data-ttu-id="331d8-233">Prima di continuare, il materiale **M_ChessKing** (M_ScacchiRe) deve essere simile all'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="331d8-233">Your **M_ChessKing** material should look like the following image before continuing.</span></span>

![Creare il materiale per il re degli scacchi](images/unreal-uxt/2-chesskingmat.PNG)

<span data-ttu-id="331d8-235">Hai quasi finito: ora basta aggiungere il nuovo pezzo degli scacchi alla scena:</span><span class="sxs-lookup"><span data-stu-id="331d8-235">You're almost there, just need to add the new chess piece into the scene:</span></span> 

1. <span data-ttu-id="331d8-236">Apri il progetto **WhiteKing** (ReBianco) e imposta **Scale** (Scala) su **(0.05, 0.05, 0.05)** e **Z Rotation** (Rotazione Z) su **90**.</span><span class="sxs-lookup"><span data-stu-id="331d8-236">Open the **WhiteKing** blueprint and change the **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span>
    * <span data-ttu-id="331d8-237">Compila e salva il progetto e quindi torna alla finestra principale.</span><span class="sxs-lookup"><span data-stu-id="331d8-237">Compile and save your blueprint, then head back to the main window.</span></span> 

2.  <span data-ttu-id="331d8-238">Trascina **WhiteKing** (ReBianco) nel viewport, passa al pannello **World Outliner** (Delinatore mondo reale) e trascina **WhiteKing** (ReBianco) su **Board** (Tavola) per renderlo un oggetto figlio.</span><span class="sxs-lookup"><span data-stu-id="331d8-238">Drag **WhiteKing** into the viewport, switch to the **World Outliner** panel drag **WhiteKing** onto **Board** to make it a child object.</span></span>

![Delineatore mondo reale](images/unreal-uxt/2-child.PNG)

3.  <span data-ttu-id="331d8-240">Nel pannello **Details** (Dettagli) in **Transform** (Trasformazione) imposta **Location** (Posizione) di **WhiteKing** (ReBianco) su **X = -26**, **Y = 4** e **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="331d8-240">In the **Details** panel under **Transform**, set **WhiteKing**'s **Location** to **X = -26**, **Y = 4**, and **Z = 0**.</span></span>

<span data-ttu-id="331d8-241">Ecco fatto!</span><span class="sxs-lookup"><span data-stu-id="331d8-241">That's a wrap!</span></span> <span data-ttu-id="331d8-242">Fai clic su **Play** (Riproduci) per vedere in azione il livello popolato, quindi premi **ESC** quando vuoi uscire.</span><span class="sxs-lookup"><span data-stu-id="331d8-242">Click **Play** to see your populated level in action, and press **Esc** when you're ready to exit.</span></span> <span data-ttu-id="331d8-243">In questa esercitazione sono stati illustrati molti aspetti relativi alla creazione di un progetto semplice, ma il tuo progetto ora è pronto per passare alla parte successiva della serie, dedicata alla configurazione per la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="331d8-243">This tutorial covered a lot of ground creating a simple project, but your project is ready to move on to the next part of the series: setting up for mixed reality.</span></span> 

[<span data-ttu-id="331d8-244">Sezione successiva: 3. Configurare il progetto per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="331d8-244">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)
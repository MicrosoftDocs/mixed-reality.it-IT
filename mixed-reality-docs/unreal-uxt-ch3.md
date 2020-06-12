---
title: 3. Configurazione del progetto per la realtà mista
description: Parte 3 di 6 in una serie di esercitazioni per la creazione di una semplice app di scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione
ms.openlocfilehash: d22c3d8c9048f53171298642768877d7bcdcb972
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330293"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a><span data-ttu-id="ec5b6-104">3. Configurazione del progetto per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="ec5b6-104">3. Setting up your project for mixed reality</span></span>

## <a name="overview"></a><span data-ttu-id="ec5b6-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="ec5b6-105">Overview</span></span>

<span data-ttu-id="ec5b6-106">Nell'esercitazione precedente ti sei dedicato alla configurazione del progetto dell'app di scacchi.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-106">In the previous tutorial, you spent time setting up the chess app project.</span></span> <span data-ttu-id="ec5b6-107">In questa sezione viene illustrato come configurare l'app per lo sviluppo in realtà mista, ovvero aggiungendo una sessione AR.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-107">This section is going to walk you through setting up the app for mixed reality development, which means adding an AR session.</span></span> <span data-ttu-id="ec5b6-108">Per questa attività userai un asset di dati ARSessionConfig che include numerose impostazioni AR utili come il mapping spaziale e l'occlusione.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-108">You'll be using an ARSessionConfig data asset for this task, which has a lot of useful AR settings like spatial mapping and occlusion.</span></span> <span data-ttu-id="ec5b6-109">Se vuoi approfondire questo argomento, la documentazione di Unreal Engine contiene altri dettagli sull'asset [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) e sulla classe [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html).</span><span class="sxs-lookup"><span data-stu-id="ec5b6-109">If you want to dive deeper, the Unreal Engine documentation has more details on the [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) asset and the [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) class.</span></span>

## <a name="objectives"></a><span data-ttu-id="ec5b6-110">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="ec5b6-110">Objectives</span></span>
* <span data-ttu-id="ec5b6-111">Uso delle impostazioni AR di Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="ec5b6-111">Working with Unreal Engine's AR settings</span></span> 
* <span data-ttu-id="ec5b6-112">Uso di un asset di dati ARSessionConfig</span><span class="sxs-lookup"><span data-stu-id="ec5b6-112">Using an ARSessionConfig data asset</span></span>
* <span data-ttu-id="ec5b6-113">Configurazione di un pedone e modalità di gioco</span><span class="sxs-lookup"><span data-stu-id="ec5b6-113">Setting up a Pawn and game mode</span></span>

## <a name="adding-the-session-asset"></a><span data-ttu-id="ec5b6-114">Aggiunta dell'asset della sessione</span><span class="sxs-lookup"><span data-stu-id="ec5b6-114">Adding the session asset</span></span>
<span data-ttu-id="ec5b6-115">Le sessioni AR in Unreal non funzionano da sole.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-115">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="ec5b6-116">Per usare una sessione, è necessario un asset di dati ARSessionConfig con cui interagire, che costituisce la tua prossima attività:</span><span class="sxs-lookup"><span data-stu-id="ec5b6-116">To use a session you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="ec5b6-117">Fai clic su **Add New > Miscellaneous > Data Asset** (Aggiungi nuovo > Varie > Asset dati) in **Content Browser** (Browser contenuto).</span><span class="sxs-lookup"><span data-stu-id="ec5b6-117">Click **Add New > Miscellaneous > Data Asset** in the **Content Browser**.</span></span> <span data-ttu-id="ec5b6-118">Assicurati di essere nella cartella **Content** radice.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-118">Make sure you're at the root **Content** folder level.</span></span> 
    * <span data-ttu-id="ec5b6-119">Seleziona **ARSessionConfig**, fai clic su **Select** (Seleziona) e assegna all'asset il nome **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-119">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**.</span></span>

![Creazione di un'origine dati](images/unreal-uxt/3-createasset.PNG)

3. <span data-ttu-id="ec5b6-121">Fai doppio clic su **ARSessionConfig** per aprirlo, lascia tutte le impostazioni predefinite e premi **Save** (Salva).</span><span class="sxs-lookup"><span data-stu-id="ec5b6-121">Double-click **ARSessionConfig** to open it, leave all default settings and hit **Save**.</span></span> <span data-ttu-id="ec5b6-122">Torna alla finestra principale.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-122">Return to the Main window.</span></span> 

![ARSessionConfig](images/unreal-uxt/3-arsessionconfig.PNG)

<span data-ttu-id="ec5b6-124">Al termine, il passaggio successivo consiste nell'assicurarsi che la sessione AR venga avviata quando viene caricato il livello.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-124">With that done, your next step is to make sure that the AR session starts when the level loads.</span></span> <span data-ttu-id="ec5b6-125">In Unreal è disponibile un particolare tipo di progetto denominato **Level Blueprint** (Progetto livello) che svolge la funzione di grafico eventi globale che prende come riferimento il livello.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-125">Luckily, Unreal has a special kind of blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="ec5b6-126">La connessione dell'asset ARSessionConfig in **Level Blueprint** (Progetto livello) garantisce l'avvio della sessione nel momento in cui viene avviato il gioco.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-126">Connecting the ARSessionConfig asset in the **Level Blueprint** guarantees the AR session will fire right when the game starts playing.</span></span>

1. <span data-ttu-id="ec5b6-127">Fai clic su **Blueprints > Open Level Blueprint** (Progetti > Apri progetto livello) sulla barra degli strumenti dell'editor:</span><span class="sxs-lookup"><span data-stu-id="ec5b6-127">Click **Blueprints > Open Level Blueprint** from the editor toolbar:</span></span> 

![Open Level Blueprint (Apri progetto livello)](images/unreal-uxt/3-level-blueprint.PNG)

5. <span data-ttu-id="ec5b6-129">Trascina il nodo di esecuzione (freccia rivolta verso sinistra) fuori da **Event BeginPlay** (Evento BeginPlay) e rilascia.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-129">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release.</span></span> <span data-ttu-id="ec5b6-130">Cerca il nodo **Start AR Session** (Avvia sessione AR) e premi INVIO.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-130">Search for the **Start AR Session** and hit enter.</span></span>  
    * <span data-ttu-id="ec5b6-131">Fai clic sull'elenco a discesa **Select Asset** (Seleziona asset) in **Session Config** (Configurazione sessione) e scegli l'asset **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-131">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset.</span></span> 
    * <span data-ttu-id="ec5b6-132">Seleziona **Compile** (Compila) e **Save** (Salva) e torna alla finestra principale.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-132">Hit **Compile**, then **Save** and return to the Main window.</span></span>

![Start AR Session (Avvia sessione AR)](images/unreal-uxt/3-start-ar-session.PNG)

## <a name="create-a-pawn"></a><span data-ttu-id="ec5b6-134">Creare un pedone</span><span class="sxs-lookup"><span data-stu-id="ec5b6-134">Create a Pawn</span></span>
<span data-ttu-id="ec5b6-135">A questo punto, il progetto necessita ancora di un oggetto Player.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-135">At this point, the project still needs a player object.</span></span> <span data-ttu-id="ec5b6-136">In Unreal, l'oggetto **Pawn** (Pedone) rappresenta l'utente del gioco, ma in questo caso sarà l'esperienza HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-136">In Unreal, a **Pawn** represents the user in the game, but in this case it's going to be the HoloLens 2 experience.</span></span>

1. <span data-ttu-id="ec5b6-137">Fai clic su **Add New > Blueprint Class** (Aggiungi nuovo > Classe progetto) nella cartella **Content** ed espandi la sezione **All Classes** (Tutte le classi) in fondo.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-137">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="ec5b6-138">Cerca **DefaultPawn**, fai clic su **Select** (Seleziona) e fai doppio clic sull'asset per aprirlo.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-138">Search for **DefaultPawn**, click **Select** and double-click the asset to open.</span></span> 

![Creare un nuovo pedone basato su DefaultPawn](images/unreal-uxt/3-defaultpawn.PNG)

> [!NOTE]
> <span data-ttu-id="ec5b6-140">Per impostazione predefinita, i pedoni hanno componenti mesh e collisione.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-140">By default, Pawns have mesh and collision components.</span></span> <span data-ttu-id="ec5b6-141">Nella maggior parte dei progetti Unreal, i pedoni sono oggetti solidi che possono collidere con altri componenti.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-141">In most Unreal projects, Pawns are solid objects that can collide with other components.</span></span> <span data-ttu-id="ec5b6-142">Dato che il pedone e l'utente coincidono nella realtà mista, è necessario poter passare attraverso gli ologrammi senza collisioni.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-142">Since the Pawn and user are the same in mixed reality, you want to be able to pass through holograms without any collisions.</span></span> 

2. <span data-ttu-id="ec5b6-143">Seleziona **CollisionComponent** nel pannello **Components** (Componenti) e scorri fino alla sezione **Collision** (Collisione) del pannello **Details** (Dettagli).</span><span class="sxs-lookup"><span data-stu-id="ec5b6-143">Select **CollisionComponent** from the **Components** panel and scroll down to the **Collision** section of the **Details** panel.</span></span> 
    * <span data-ttu-id="ec5b6-144">Fai clic sull'elenco a discesa **Collision Presets** (Set di impostazioni di collisione) e cambia il valore in **NoCollision**.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-144">Click the **Collision Presets** dropdown and change the value to **NoCollision**.</span></span> 
    * <span data-ttu-id="ec5b6-145">Esegui la stessa operazione per **MeshComponent** e fai clic su **Compile** (Compila) e **Save** (Salva) per salvare il progetto.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-145">Do the same for the **MeshComponent**, then **Compile** and **Save** the Blueprint.</span></span> 

![Modifica dei set di impostazioni di collisione del pedone](images/unreal-uxt/3-nocollision.PNG)

<span data-ttu-id="ec5b6-147">Al termine, torna alla finestra principale.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-147">With your work here done, return to the Main Window.</span></span>

## <a name="create-a-game-mode"></a><span data-ttu-id="ec5b6-148">Creare una modalità di gioco</span><span class="sxs-lookup"><span data-stu-id="ec5b6-148">Create a Game Mode</span></span>
<span data-ttu-id="ec5b6-149">Per completare la configurazione della realtà mista manca solo la modalità di gioco.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-149">The last puzzle piece of the mixed reality setup is the Game Mode.</span></span> <span data-ttu-id="ec5b6-150">La modalità di gioco determina una serie di impostazioni relative al gioco o all'esperienza, incluso il pedone predefinito da usare.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-150">The Game Mode determines a number of settings for the game or experience, including the default pawn to use.</span></span>

1.  <span data-ttu-id="ec5b6-151">Fai clic su **Add New > Blueprint Class** (Aggiungi nuovo > Classe progetto) nella cartella **Content** (Contenuto) ed espandi la sezione **All Classes** (Tutte le classi) in fondo.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-151">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="ec5b6-152">Cerca **Game Mode Base** (Base modalità gioco), assegna il nome **MRGameMode** e fai doppio clic per aprire l'elemento.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-152">Search for **Game Mode Base**, name it **MRGameMode** and double-click to open.</span></span> 

![MRGameMode nel browser dei contenuti](images/unreal-uxt/3-gamemode.PNG)

2.  <span data-ttu-id="ec5b6-154">Passa alla sezione **Classes** (Classi) nel pannello **Details** (Dettagli) e modifica **Default Pawn Class** (Classe pedone predefinito) in **MRPawn**.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-154">Go to the **Classes** section in the **Details** panel and change the **Default Pawn Class** to **MRPawn**.</span></span> 
    * <span data-ttu-id="ec5b6-155">Seleziona **Compile** (Compila) e **Save** (Salva) e torna alla finestra principale.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-155">Hit **Compile**, then **Save** and return to the Main window.</span></span> 

![Impostazione della classe di pedone predefinita](images/unreal-uxt/3-setpawn.PNG)

3.  <span data-ttu-id="ec5b6-157">Seleziona **Edit > Projects Settings** (Modifica > Impostazioni progetti) e fai clic su **Maps & Modes** (Mappe e modalità) nell'elenco a sinistra.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-157">Select **Edit > Projects Settings** and click **Maps & Modes** in the left-hand list.</span></span> 
    * <span data-ttu-id="ec5b6-158">Espandi **Default Modes** (Modalità predefinite) e cambia **Default Game Mode** (Modalità gioco predefinita) in **MRGameMode**.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-158">Expand **Default Modes** and change **Default Game Mode** to **MRGameMode**.</span></span> 
    * <span data-ttu-id="ec5b6-159">Espandi **Default Maps** (Mappe predefinite) e imposta sia **EditorStartupMap** sia **GameDefaultMap** su **Main** (Principale).</span><span class="sxs-lookup"><span data-stu-id="ec5b6-159">Expand **Default Maps** and change both **EditorStartupMap** and **GameDefaultMap** to **Main**.</span></span> <span data-ttu-id="ec5b6-160">In questo modo, quando si chiude e si riapre l'editor o si usa il gioco, per impostazione predefinita viene selezionata la mappa principale.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-160">This way when you close and reopen the editor, or play the game, the Main map will be selected by default.</span></span>

![Project Settings - Maps & Modes (Impostazioni progetto - Mappe e modalità)](images/unreal-uxt/3-mapsandmodes.PNG)

<span data-ttu-id="ec5b6-162">Dopo avere completato la configurazione del progetto per la realtà mista, puoi passare all'esercitazione successiva e iniziare ad aggiungere input utente alla scena.</span><span class="sxs-lookup"><span data-stu-id="ec5b6-162">With the project fully setup for mixed reality, you're ready to move on to the next tutorial and start adding user input to the scene.</span></span> 

[<span data-ttu-id="ec5b6-163">Sezione successiva: 4. Rendere la scena interattiva</span><span class="sxs-lookup"><span data-stu-id="ec5b6-163">Next Section: 4. Making your scene interactive</span></span>](unreal-uxt-ch4.md)
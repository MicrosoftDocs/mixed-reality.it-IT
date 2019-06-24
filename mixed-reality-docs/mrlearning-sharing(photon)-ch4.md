---
title: MR Learning condivisione del modulo per HoloLens 2
description: Completare questo corso di informazioni su come implementare esperienze condivise con più utenti all'interno di un'applicazione 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: a67eaef45582054b62198a563f0ee01724fd60db
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326621"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a><span data-ttu-id="070b6-104">La sincronizzazione gli spostamenti degli oggetti condivisi</span><span class="sxs-lookup"><span data-stu-id="070b6-104">Synchronizing the Movements of Shared Objects</span></span>

<span data-ttu-id="070b6-105">In questa lezione si apprenderà come condividere gli spostamenti degli oggetti in modo che tutti i partecipanti di una sessione condivisa è possono collaborare insieme e visualizzare le interazioni degli altri.</span><span class="sxs-lookup"><span data-stu-id="070b6-105">In this lesson, we will learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="070b6-106">Questa lezione si basa l'utilità di avvio lunare che è stato compilato come parte del [esercitazioni di modulo Base](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="070b6-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="070b6-107">Obiettivi:</span><span class="sxs-lookup"><span data-stu-id="070b6-107">Objectives:</span></span>

- <span data-ttu-id="070b6-108">Importare l'utilità di avvio lunare completata come il modello 3D da condividere</span><span class="sxs-lookup"><span data-stu-id="070b6-108">Import the completed Lunar Launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="070b6-109">Configurare il progetto per condividere i movimenti del modello 3D.</span><span class="sxs-lookup"><span data-stu-id="070b6-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="070b6-110">Informazioni su come compilare un'applicazione di collaborazione multiutente base</span><span class="sxs-lookup"><span data-stu-id="070b6-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="070b6-111">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="070b6-111">Instructions</span></span>

1. <span data-ttu-id="070b6-112">Salvare la scena nella lezione precedente (CTRL + S).</span><span class="sxs-lookup"><span data-stu-id="070b6-112">Save the scene from the previous lesson (control+S).</span></span> <span data-ttu-id="070b6-113">È possibile denominarlo "HLSharedProjectMainPart4.unity" in modo che risulti più facile individuare quando è necessario.</span><span class="sxs-lookup"><span data-stu-id="070b6-113">You may name it "HLSharedProjectMainPart4.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="070b6-114">Eliminare l'oggetto "NetworkLobby" (selezionandolo e premendo CANC).</span><span class="sxs-lookup"><span data-stu-id="070b6-114">Delete the "NetworkLobby" object (by selecting it and pressing delete).</span></span> <span data-ttu-id="070b6-115">Inoltre, passare alla cartella "prefabs" creato nella lezione 2 ed eliminare il prefab "NetworkLobby" anche dal.</span><span class="sxs-lookup"><span data-stu-id="070b6-115">Also, go into the "prefabs" folder from lesson 2 and delete the "NetworkLobby" prefab from there as well.</span></span>

![Module3Chapter4tep2im](images/module3chapter4step2im.PNG)

3. <span data-ttu-id="070b6-117">Importare un nuovo pacchetto personalizzato (ad esempio, passaggio 2 nella lezione 2) e importare il [LunarModule.unitypackage](linkforModule1 lesson with the lunar module) e il [NetworkLobbyReplacement.unitypackage.](linkforNetworklobbyreplacement package here)</span><span class="sxs-lookup"><span data-stu-id="070b6-117">Import a new custom package (like step 2 from the lesson 2) and import the [LunarModule.unitypackage](linkforModule1 lesson with the lunar module) and the [NetworkLobbyReplacement.unitypackage.](linkforNetworklobbyreplacement package here)</span></span>

![Module3Chapter4step3im](images/module3chapter4step3im.PNG)

4. <span data-ttu-id="070b6-119">A questo punto, nella cartella "prefabs", trascinare il prefab "NetworkLobby" nuovo nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="070b6-119">Now, in the "prefabs" folder, drag the new "NetworkLobby" prefab into the hierarchy .</span></span> 

![Module3hapter4step4im](images/module3chapter4step4im.PNG)

> <span data-ttu-id="070b6-121">Nota: i due pacchetti sono stati importati nei passaggi precedenti aggiornati il prefab "NetworkLobby".</span><span class="sxs-lookup"><span data-stu-id="070b6-121">note: the two packages we imported in the previous steps updated the "NetworkLobby" prefab.</span></span> <span data-ttu-id="070b6-122">Evita di molta digitazione.</span><span class="sxs-lookup"><span data-stu-id="070b6-122">It saves you from a lot of typing!</span></span>

5. <span data-ttu-id="070b6-123">A questo punto, fare clic sulla freccia a sinistra di "MixedRealityPlayspace" e spostare l'oggetto gioco figlio, "MainCamera" verso il basso nel prefab "SharedPlayground".</span><span class="sxs-lookup"><span data-stu-id="070b6-123">Now, click the arrow to the left of "MixedRealityPlayspace" and move the child game object, "MainCamera" down into the "SharedPlayground" prefab.</span></span> <span data-ttu-id="070b6-124">Eliminare quindi il prefab "MixedRealityPlayspace" (per eliminare, selezionare il prefab e toccare "Elimina" sulla tastiera).</span><span class="sxs-lookup"><span data-stu-id="070b6-124">Then, delete the prefab "MixedRealityPlayspace" (to delete, select the prefab and tap "delete" on your keyboard).</span></span>

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

6. <span data-ttu-id="070b6-126">Creare un nuovo oggetto gioco impostata come un oggetto figlio all'oggetto padre "SharedPlayground" (per creare un nuovo oggetto, fare clic con il pulsante destro sull'oggetto padre e selezionare "Crea vuoto").</span><span class="sxs-lookup"><span data-stu-id="070b6-126">Create a new game object set as a child object to the "SharedPlayground" parent object (to create a new object, right click on the parent object, and select "create  empty").</span></span>
7. <span data-ttu-id="070b6-127">Con il nuovo oggetto selezionato nella gerarchia, è possibile modificare il nome dell'oggetto in "TableAnchor" nel Pannello di controllo.</span><span class="sxs-lookup"><span data-stu-id="070b6-127">With the new object selected in your hierarchy, change the name of the object to "TableAnchor" in the inspector panel.</span></span> <span data-ttu-id="070b6-128">Inoltre, fare clic su "Aggiungi componente" e cercare il componente "TableAnchor".</span><span class="sxs-lookup"><span data-stu-id="070b6-128">Also, click "add component" and search for the "TableAnchor" component.</span></span> <span data-ttu-id="070b6-129">Selezionarlo e aggiungerlo all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="070b6-129">Select it and add it to the object.</span></span>

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="070b6-131">Nota: impostare il posizionamento su x = 1, y =-0,55 e z = 2.</span><span class="sxs-lookup"><span data-stu-id="070b6-131">note: set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="070b6-132">Inoltre, impostare la rotazione di y = 90.</span><span class="sxs-lookup"><span data-stu-id="070b6-132">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

8. <span data-ttu-id="070b6-134">Nel Pannello di progetto, nella cartella "prefabs", trascinare ora il prefab "table" nell'oggetto figlio "TableAnchor" appena creato.</span><span class="sxs-lookup"><span data-stu-id="070b6-134">Now in the project panel, in the "prefabs" folder, drag the "table" prefab into the "TableAnchor" child object you just created.</span></span>

   ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

9. <span data-ttu-id="070b6-136">Selezionare "NetworkRoom", un oggetto figlio sotto "NetworkLobby" nella gerarchia e fare clic su "Aggiungi componente" nel Pannello di controllo e cercare "PhotonView" e aggiungere lo script per il "*NetworkRoom*" oggetti.</span><span class="sxs-lookup"><span data-stu-id="070b6-136">Select "NetworkRoom," a child object under "NetworkLobby" in the hierachy, and click "add component" in the inspector panel and search for "PhotonView" and add the script to the "*NetworkRoom*" object.</span></span>

![Module3Chapter4step9im](images/module3chapter4step9im.PNG)

11. <span data-ttu-id="070b6-138">Infine, nell'oggetto "DebugWindow", modificare la larghezza a 80 e l'altezza su 10.</span><span class="sxs-lookup"><span data-stu-id="070b6-138">Finally, in the "DebugWindow" object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="070b6-140">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="070b6-140">Congratulations</span></span>

<span data-ttu-id="070b6-141">Al termine, tutti gli utenti che eseguono join di un progetto Unity possono spostarsi l'utilità di avvio lunare.</span><span class="sxs-lookup"><span data-stu-id="070b6-141">Once this is complete, all users that join your Unity project can move the Lunar Launcher around.</span></span> <span data-ttu-id="070b6-142">Tutti gli spostamenti siano sincronizzati affinché ogni utente può visualizzare le interazioni degli altri.</span><span class="sxs-lookup"><span data-stu-id="070b6-142">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="070b6-143">Questi concetti può essere utilizzato come i blocchi predefiniti fondamentali per le esperienze complete collaborazione condiviso.</span><span class="sxs-lookup"><span data-stu-id="070b6-143">These concepts serve as the foundational building blocks for full-featured shared collaboration experiences.</span></span> 

<span data-ttu-id="070b6-144">Anche se tutti gli utenti connessi come parte di un'esperienza condivisa e vede i movimenti relativi degli oggetti, l'applicazione non riesce ancora a allineare accuratamente gli avatar e gli oggetti in modo che gli utenti locali vedono tra loro e gli oggetti nella stessa posizione all'interno di fisico World.</span><span class="sxs-lookup"><span data-stu-id="070b6-144">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="070b6-145">Per ancorare un esperienze condivise locale, tutti i dispositivi richiede una conoscenza comune dell'ambiente fisico.</span><span class="sxs-lookup"><span data-stu-id="070b6-145">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="070b6-146">In questo modulo a tale scopo mediante [Anchor spaziali Azure](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), che verrà implementato nella lezione successiva.</span><span class="sxs-lookup"><span data-stu-id="070b6-146">In this module, we will achieve this using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), which will be implemented in the next lesson.</span></span>

<span data-ttu-id="070b6-147">Prima di procedere alla lezione successiva, è necessario completare il modulo di apprendimento ASA, che si occuperà nozioni di base ASA, account di Azure e la creazione di risorse e altri blocchi di edifici fondamentali necessarie prima che è possibile integrare questa funzionalità nella nostra esperienza condiviso.</span><span class="sxs-lookup"><span data-stu-id="070b6-147">Before proceeding to the next lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="070b6-148">[Lezione successiva: Sharing(photon) lezione 5](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="070b6-148">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>


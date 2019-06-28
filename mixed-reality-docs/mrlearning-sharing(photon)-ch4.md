---
title: MR Learning condivisione del modulo per HoloLens 2
description: Completare questo corso di informazioni su come implementare esperienze condivise con più utenti all'interno di un'applicazione 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: d5bed61f5ffc1d3b4efed96f47c3568fbf3a2948
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416012"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a><span data-ttu-id="5f73a-104">La sincronizzazione gli spostamenti degli oggetti condivisi</span><span class="sxs-lookup"><span data-stu-id="5f73a-104">Synchronizing the Movements of Shared Objects</span></span>

<span data-ttu-id="5f73a-105">In questa lezione si apprenderà come condividere gli spostamenti degli oggetti in modo che tutti i partecipanti di una sessione condivisa è possono collaborare insieme e visualizzare le interazioni degli altri.</span><span class="sxs-lookup"><span data-stu-id="5f73a-105">In this lesson, we will learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="5f73a-106">Questa lezione si basa l'utilità di avvio lunare che è stato compilato come parte del [esercitazioni di modulo Base](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="5f73a-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="5f73a-107">Obiettivi:</span><span class="sxs-lookup"><span data-stu-id="5f73a-107">Objectives:</span></span>

- <span data-ttu-id="5f73a-108">Portare nell'utilità di avvio lunare come il modello 3D da condividere</span><span class="sxs-lookup"><span data-stu-id="5f73a-108">Bring in the Lunar Launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="5f73a-109">Configurare il progetto per condividere i movimenti del modello 3D.</span><span class="sxs-lookup"><span data-stu-id="5f73a-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="5f73a-110">Informazioni su come compilare un'applicazione di collaborazione multiutente base</span><span class="sxs-lookup"><span data-stu-id="5f73a-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="5f73a-111">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="5f73a-111">Instructions</span></span>

1. <span data-ttu-id="5f73a-112">Salvare la scena nella lezione precedente (CTRL + S).</span><span class="sxs-lookup"><span data-stu-id="5f73a-112">Save the scene from the previous lesson (control+S).</span></span> <span data-ttu-id="5f73a-113">È possibile denominarlo "HLSharedProjectMainPart4.unity" in modo che risulti più facile individuare quando è necessario.</span><span class="sxs-lookup"><span data-stu-id="5f73a-113">You may name it "HLSharedProjectMainPart4.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="5f73a-114">Nella finestra del progetto, negli asset > cartella degli script, fare doppio clic sul GenericNetSync per aprirlo in Visual Studio o che mai code editor in uso.</span><span class="sxs-lookup"><span data-stu-id="5f73a-114">In the Project window, in the Assets > Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  ![](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="5f73a-115">Nelle righe 34 e 38, rimuovere il "/ /" per attivare il codice per la tabella che verrà usato in questa lezione.</span><span class="sxs-lookup"><span data-stu-id="5f73a-115">On lines 34 and 38, remove the "//" to activate the code for the Table that we will use in this lesson.</span></span>  <span data-ttu-id="5f73a-116">Quindi salvare il file.</span><span class="sxs-lookup"><span data-stu-id="5f73a-116">Then Save the file.</span></span> ![](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="5f73a-117">Nella finestra del progetto, fare doppio clic sul file PhotonRoom.cs negli asset > cartella Scripts per aprirla nuovamente in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5f73a-117">In the project window, double click on the PhotonRoom.cs file in the Assets > Scripts folder to again open it in Visual Studio.</span></span> ![](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="5f73a-118">Proprio come nel passaggio 3 è necessario rimuovere il "/ /" per attivare il codice alla righe 26, 25 e 106.![](images/module3chapter4updatestep5a.png)</span><span class="sxs-lookup"><span data-stu-id="5f73a-118">Just like in step 3 we need to remove the "//" to activate the code at lines 25, 26, and 106.![](images/module3chapter4updatestep5a.png)</span></span> ![](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="5f73a-119">Nella visualizzazione gerarchia, selezionare l'oggetto NetworkRoom.![](images/module3chapter4updatestep6.png)</span><span class="sxs-lookup"><span data-stu-id="5f73a-119">In the Hierarchy view, select the NetworkRoom object.![](images/module3chapter4updatestep6.png)</span></span>

7. <span data-ttu-id="5f73a-120">Nella visualizzazione del progetto, passare a asset > risorse > Prefabs.</span><span class="sxs-lookup"><span data-stu-id="5f73a-120">In the project view, navigate to Assets > Resources > Prefabs.</span></span> <span data-ttu-id="5f73a-121">In primo luogo, trascinare e rilasciare il prefab tabella allo slot di "Tableprefab" nella classe PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="5f73a-121">First, drag and drop the Table prefab to the "Tableprefab" slot on the PhotonRoom class.</span></span> <span data-ttu-id="5f73a-122">Trascinare quindi il prefab LunarModule allo slot di "Modulo Prefab" nella classe PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="5f73a-122">Next drag and drop the LunarModule prefab to the "Module Prefab" slot on the PhotonRoom class.</span></span> ![](images/module3chapter4updatestep7.png)

   <span data-ttu-id="5f73a-123">Nota: Se si fa clic su uno degli oggetti prefab e versione, il controllo passerà a quell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="5f73a-123">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="5f73a-124">Fare clic su, trascinare e rilasciare ogni oggetto al relativo slot appropriato.</span><span class="sxs-lookup"><span data-stu-id="5f73a-124">Click, drag, drop and release each object to its appropriate slot.</span></span>



8. <span data-ttu-id="5f73a-125">A questo punto, fare clic sulla freccia a sinistra di "MixedRealityPlayspace" e spostare l'oggetto gioco figlio, "MainCamera" verso il basso nel prefab "SharedPlayground".</span><span class="sxs-lookup"><span data-stu-id="5f73a-125">Now, click the arrow to the left of "MixedRealityPlayspace" and move the child game object, "MainCamera" down into the "SharedPlayground" prefab.</span></span> <span data-ttu-id="5f73a-126">Eliminare quindi il prefab "MixedRealityPlayspace" (per eliminare, selezionare il prefab e toccare "Elimina" sulla tastiera).</span><span class="sxs-lookup"><span data-stu-id="5f73a-126">Then, delete the prefab "MixedRealityPlayspace" (to delete, select the prefab and tap "delete" on your keyboard).</span></span>

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

<span data-ttu-id="5f73a-128">Nota:  Assicurarsi che sia il Main Camera SharedPlayground significativi vengono impostati su 0, 0,0.</span><span class="sxs-lookup"><span data-stu-id="5f73a-128">note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="5f73a-129">Creare un nuovo oggetto gioco impostata come un oggetto figlio all'oggetto padre "SharedPlayground" (per creare un nuovo oggetto, fare clic con il pulsante destro sull'oggetto padre e selezionare "Crea vuoto").</span><span class="sxs-lookup"><span data-stu-id="5f73a-129">Create a new game object set as a child object to the "SharedPlayground" parent object (to create a new object, right click on the parent object, and select "create  empty").</span></span> 

10. <span data-ttu-id="5f73a-130">Con il nuovo oggetto selezionato nella gerarchia, è possibile modificare il nome dell'oggetto in "TableAnchor" nel Pannello di controllo.</span><span class="sxs-lookup"><span data-stu-id="5f73a-130">With the new object selected in your hierarchy, change the name of the object to "TableAnchor" in the inspector panel.</span></span> <span data-ttu-id="5f73a-131">Inoltre, fare clic su "Aggiungi componente" e cercare il componente "TableAnchor".</span><span class="sxs-lookup"><span data-stu-id="5f73a-131">Also, click "add component" and search for the "TableAnchor" component.</span></span> <span data-ttu-id="5f73a-132">Selezionarlo e aggiungerlo all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="5f73a-132">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="5f73a-134">Nota: impostare il posizionamento su x = 1, y =-0,55 e z = 2.</span><span class="sxs-lookup"><span data-stu-id="5f73a-134">note: set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="5f73a-135">Inoltre, impostare la rotazione di y = 90.</span><span class="sxs-lookup"><span data-stu-id="5f73a-135">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. <span data-ttu-id="5f73a-137">Nel Pannello di progetto, nella cartella "prefabs", trascinare ora il prefab "table" nell'oggetto figlio "TableAnchor" appena creato.</span><span class="sxs-lookup"><span data-stu-id="5f73a-137">Now in the project panel, in the "prefabs" folder, drag the "table" prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. <span data-ttu-id="5f73a-139">Infine, nell'oggetto "DebugWindow", modificare la larghezza a 80 e l'altezza su 10.</span><span class="sxs-lookup"><span data-stu-id="5f73a-139">Finally, in the "DebugWindow" object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="5f73a-141">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="5f73a-141">Congratulations</span></span>

<span data-ttu-id="5f73a-142">Al termine, tutti gli utenti che eseguono join di un progetto Unity possono spostarsi l'utilità di avvio lunare.</span><span class="sxs-lookup"><span data-stu-id="5f73a-142">Once this is complete, all users that join your Unity project can move the Lunar Launcher around.</span></span> <span data-ttu-id="5f73a-143">Tutti gli spostamenti siano sincronizzati affinché ogni utente può visualizzare le interazioni degli altri.</span><span class="sxs-lookup"><span data-stu-id="5f73a-143">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="5f73a-144">Questi concetti può essere utilizzato come i blocchi predefiniti fondamentali per le esperienze complete collaborazione condiviso.</span><span class="sxs-lookup"><span data-stu-id="5f73a-144">These concepts serve as the foundational building blocks for full-featured shared collaboration experiences.</span></span> 

<span data-ttu-id="5f73a-145">Anche se tutti gli utenti connessi come parte di un'esperienza condivisa e vede i movimenti relativi degli oggetti, l'applicazione non riesce ancora a allineare accuratamente gli avatar e gli oggetti in modo che gli utenti locali vedono tra loro e gli oggetti nella stessa posizione all'interno di fisico World.</span><span class="sxs-lookup"><span data-stu-id="5f73a-145">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="5f73a-146">Per ancorare un esperienze condivise locale, tutti i dispositivi richiede una conoscenza comune dell'ambiente fisico.</span><span class="sxs-lookup"><span data-stu-id="5f73a-146">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="5f73a-147">In questo modulo a tale scopo mediante [Anchor spaziali Azure](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), che verrà implementato nella lezione successiva.</span><span class="sxs-lookup"><span data-stu-id="5f73a-147">In this module, we will achieve this using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), which will be implemented in the next lesson.</span></span>

<span data-ttu-id="5f73a-148">Prima di procedere alla lezione successiva, è necessario completare il modulo di apprendimento ASA, che si occuperà nozioni di base ASA, account di Azure e la creazione di risorse e altri blocchi di edifici fondamentali necessarie prima che è possibile integrare questa funzionalità nella nostra esperienza condiviso.</span><span class="sxs-lookup"><span data-stu-id="5f73a-148">Before proceeding to the next lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="5f73a-149">[Lezione successiva: Sharing(photon) lezione 5](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="5f73a-149">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>


---
title: MR Learning condivisione del modulo per HoloLens 2
description: Completare questo corso di informazioni su come implementare esperienze condivise con più utenti all'interno di un'applicazione 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: b729de818dfa21df8fbce782a24a611a365ac795
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465228"
---
# <a name="synchronizing-shared-object-movements"></a><span data-ttu-id="5649f-104">La sincronizzazione gli spostamenti di oggetti condivisi</span><span class="sxs-lookup"><span data-stu-id="5649f-104">Synchronizing shared object movements</span></span>

<span data-ttu-id="5649f-105">In questa lezione, abbiamo illustrato come condividere gli spostamenti degli oggetti in modo che tutti i partecipanti di una sessione condivisa è possono collaborare insieme e visualizzare le interazioni degli altri.</span><span class="sxs-lookup"><span data-stu-id="5649f-105">In this lesson, we learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="5649f-106">Questa lezione si basa l'utilità di avvio lunare che è stato compilato come parte del [esercitazioni di modulo Base](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="5649f-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="5649f-107">Obiettivi:</span><span class="sxs-lookup"><span data-stu-id="5649f-107">Objectives:</span></span>

- <span data-ttu-id="5649f-108">Portare nell'utilità di avvio lunare come il modello 3D da condividere</span><span class="sxs-lookup"><span data-stu-id="5649f-108">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="5649f-109">Configurare il progetto per condividere i movimenti del modello 3D.</span><span class="sxs-lookup"><span data-stu-id="5649f-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="5649f-110">Informazioni su come compilare un'applicazione di collaborazione multiutente base</span><span class="sxs-lookup"><span data-stu-id="5649f-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="5649f-111">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="5649f-111">Instructions</span></span>


1. <span data-ttu-id="5649f-112">Salvare la scena nella lezione precedente (CTRL + + S).</span><span class="sxs-lookup"><span data-stu-id="5649f-112">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="5649f-113">È possibile specificare un nome HLSharedProjectMainPart4.unity in modo che risulti più semplice trovare quando ti serve.</span><span class="sxs-lookup"><span data-stu-id="5649f-113">You can name it HLSharedProjectMainPart4.unity so that it's easier to find when you need it.</span></span>

2. <span data-ttu-id="5649f-114">Nella finestra del progetto negli asset -> cartella degli script, fare doppio clic su GenericNetSync per aprirlo in Visual Studio o che mai code editor in uso.</span><span class="sxs-lookup"><span data-stu-id="5649f-114">From the Project window, in the Assets->Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  ![](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="5649f-115">Nelle righe 34 e 38, rimuovere il / / per attivare il codice per la tabella che verrà usato in questa lezione.</span><span class="sxs-lookup"><span data-stu-id="5649f-115">On Lines 34 and 38, remove the // to activate the code for the table that we will use in this lesson.</span></span> <span data-ttu-id="5649f-116">Successivamente, salvare il file.</span><span class="sxs-lookup"><span data-stu-id="5649f-116">next, Save the file.</span></span> ![](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="5649f-117">Nella finestra del progetto, fare doppio clic sul file PhotonRoom.cs negli asset -> cartella Scripts per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5649f-117">In the Project window, double click on the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span> ![](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="5649f-118">Proprio come nel passaggio 3, è necessario rimuovere il / / per attivare il codice alla righe 26, 25 e 106.![](images/module3chapter4updatestep5a.png)</span><span class="sxs-lookup"><span data-stu-id="5649f-118">Just like in Step 3, we need to remove the // to activate the code at Lines 25, 26, and 106.![](images/module3chapter4updatestep5a.png)</span></span> ![](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="5649f-119">Nella visualizzazione gerarchia, selezionare l'oggetto NetworkRoom.![](images/module3chapter4updatestep6.png)</span><span class="sxs-lookup"><span data-stu-id="5649f-119">In the Hierarchy view, select the NetworkRoom object.![](images/module3chapter4updatestep6.png)</span></span>

7. <span data-ttu-id="5649f-120">Nella visualizzazione del progetto, passare a asset -> risorse -> Prefabs.</span><span class="sxs-lookup"><span data-stu-id="5649f-120">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="5649f-121">In primo luogo, trascinare e rilasciare il prefab tabella allo slot Tableprefab sulla classe PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="5649f-121">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="5649f-122">Trascinare quindi il prefab LunarModule allo slot di modulo Prefab sulla classe PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="5649f-122">Next drag and drop the LunarModule prefab to the Module Prefab slot on the PhotonRoom class.</span></span> ![](images/module3chapter4updatestep7.png)

   <span data-ttu-id="5649f-123">Nota: Se si fa clic su uno degli oggetti prefab e versione, il controllo passerà a quell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="5649f-123">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="5649f-124">Fare clic su, trascinare, rilasciare e rilasciare ogni oggetto al relativo slot appropriato.</span><span class="sxs-lookup"><span data-stu-id="5649f-124">Click, drag, drop, and release each object to its appropriate slot.</span></span>



8. <span data-ttu-id="5649f-125">Fare clic sulla freccia a sinistra del MixedRealityPlayspace e spostarvi i prefab SharedPlayground oggetto gioco figlio, MainCamera verso il basso.</span><span class="sxs-lookup"><span data-stu-id="5649f-125">Click the arrow to the left of MixedRealityPlayspace, and move the child game object, MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="5649f-126">Eliminare quindi il prefab, MixedRealityPlayspace, eliminare, selezionare il prefab e toccare "Elimina" sulla tastiera).</span><span class="sxs-lookup"><span data-stu-id="5649f-126">Next, delete the prefab, MixedRealityPlayspace, to delete, select the prefab, and tap "delete" on your keyboard).</span></span>
<span data-ttu-id="5649f-127">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span><span class="sxs-lookup"><span data-stu-id="5649f-127">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span></span>

<span data-ttu-id="5649f-128">Nota:  Assicurarsi che sia il Main Camera SharedPlayground significativi vengono impostati su 0, 0,0.</span><span class="sxs-lookup"><span data-stu-id="5649f-128">Note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="5649f-129">Creare un nuovo oggetto gioco impostata come un oggetto figlio all'oggetto padre SharedPlayground per creare un nuovo oggetto.</span><span class="sxs-lookup"><span data-stu-id="5649f-129">Create a new game object set as a child object to the SharedPlayground parent object to create a new object.</span></span> <span data-ttu-id="5649f-130">Fare clic con il pulsante destro sull'oggetto padre e selezionare Crea vuoto.</span><span class="sxs-lookup"><span data-stu-id="5649f-130">Right click on the parent object, and select Create Empty.</span></span> 

10. <span data-ttu-id="5649f-131">Con il nuovo oggetto selezionato nella gerarchia, è possibile modificare il nome dell'oggetto in TableAnchor nel Pannello di controllo.</span><span class="sxs-lookup"><span data-stu-id="5649f-131">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="5649f-132">Inoltre, fare clic su Add Component e cercare il componente TableAnchor.</span><span class="sxs-lookup"><span data-stu-id="5649f-132">Also, click Add Component, and search for the TableAnchor component.</span></span> <span data-ttu-id="5649f-133">Selezionarlo e aggiungerlo all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="5649f-133">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="5649f-135">Nota: Impostare il posizionamento su x = 1, y =-0,55 e z = 2.</span><span class="sxs-lookup"><span data-stu-id="5649f-135">Note: Set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="5649f-136">Inoltre, impostare la rotazione di y = 90.</span><span class="sxs-lookup"><span data-stu-id="5649f-136">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. <span data-ttu-id="5649f-138">Trascinare ora il prefab tabella dal Pannello di progetto nella cartella Prefabs, nell'oggetto figlio "TableAnchor" appena creato.</span><span class="sxs-lookup"><span data-stu-id="5649f-138">Now from the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. <span data-ttu-id="5649f-140">Infine, nell'oggetto DebugWindow, modificare la larghezza a 80 e l'altezza su 10.</span><span class="sxs-lookup"><span data-stu-id="5649f-140">Finally, in the DebugWindow object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="5649f-142">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="5649f-142">Congratulations</span></span>


<span data-ttu-id="5649f-143">Al termine, tutti gli utenti che eseguono join di un progetto Unity possono spostarsi l'utilità di avvio lunare.</span><span class="sxs-lookup"><span data-stu-id="5649f-143">Once this is complete, all users that join your Unity project can move the lunar launcher around.</span></span> <span data-ttu-id="5649f-144">Tutti gli spostamenti siano sincronizzati affinché ogni utente può visualizzare le interazioni degli altri.</span><span class="sxs-lookup"><span data-stu-id="5649f-144">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="5649f-145">Questi concetti può essere utilizzato come i blocchi predefiniti fondamentali per le esperienze di collaborazione completa e condivisa.</span><span class="sxs-lookup"><span data-stu-id="5649f-145">These concepts serve as the foundational building blocks for full-featured, shared collaboration experiences.</span></span> 

<span data-ttu-id="5649f-146">Anche se tutti gli utenti connessi come parte di un'esperienza condivisa e vede i movimenti relativi degli oggetti, l'applicazione non riesce ancora a allineare accuratamente gli avatar e gli oggetti in modo che gli utenti locali vedono tra loro e gli oggetti nella stessa posizione all'interno di fisico World.</span><span class="sxs-lookup"><span data-stu-id="5649f-146">Although all users are connected as part of a shared experience, and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="5649f-147">Per ancorare un esperienze condivise locale, tutti i dispositivi richiede una conoscenza comune dell'ambiente fisico.</span><span class="sxs-lookup"><span data-stu-id="5649f-147">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="5649f-148">In questo modulo, è possibile ottenere questo risultato utilizzando [Anchor spaziali Azure](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) che verranno implementati nella lezione successiva.</span><span class="sxs-lookup"><span data-stu-id="5649f-148">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) that will be implemented in the next lesson.</span></span>

<span data-ttu-id="5649f-149">Prima di procedere alla lezione successiva, è necessario completare il modulo di apprendimento ASA che copre nozioni di base ASA, account di Azure e la creazione di risorse e altri blocchi di edifici fondamentali necessarie prima che è possibile integrare questa funzionalità nella nostra esperienza condiviso.</span><span class="sxs-lookup"><span data-stu-id="5649f-149">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="5649f-150">[Lezione successiva: Sharing(photon) lezione 5](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="5649f-150">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>


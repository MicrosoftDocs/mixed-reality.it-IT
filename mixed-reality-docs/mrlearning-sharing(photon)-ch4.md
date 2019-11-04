---
title: Esercitazioni sulle funzionalità multiutente-4. Condivisione di movimenti di oggetti con più utenti
description: Completare questo corso per apprendere come implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: b4713caf2c4d913fe8f5b01c08b3cd0152e32cd9
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438362"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="9e829-105">4. condivisione di movimenti di oggetti con più utenti</span><span class="sxs-lookup"><span data-stu-id="9e829-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="9e829-106">In questa esercitazione si apprenderà come condividere i movimenti degli oggetti in modo che tutti i partecipanti di una sessione condivisa possano collaborare e visualizzare le interazioni degli altri utenti.</span><span class="sxs-lookup"><span data-stu-id="9e829-106">In this Tutorial, you'll learn how to share the movements of objects so that all participants of a shared session can collaborate and view each others' interactions.</span></span> <span data-ttu-id="9e829-107">Questa lezione si basa sull'utilità di avvio lunare compilata come parte delle [esercitazioni sul modulo di base](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="9e829-107">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="9e829-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="9e829-108">Objectives:</span></span>

- <span data-ttu-id="9e829-109">Portare il Launcher Lunar come modello 3D da condividere</span><span class="sxs-lookup"><span data-stu-id="9e829-109">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="9e829-110">Configurare il progetto per condividere i movimenti del modello 3D</span><span class="sxs-lookup"><span data-stu-id="9e829-110">Configure your project to share the movements of the 3D model</span></span>
- <span data-ttu-id="9e829-111">Informazioni su come creare un'applicazione di collaborazione multiutente di base</span><span class="sxs-lookup"><span data-stu-id="9e829-111">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="instructions"></a><span data-ttu-id="9e829-112">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="9e829-112">Instructions</span></span>


1. <span data-ttu-id="9e829-113">Salvare la scena dalla lezione precedente (CTRL + S).</span><span class="sxs-lookup"><span data-stu-id="9e829-113">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="9e829-114">È possibile denominarlo HLSharedProjectMainPart4. Unity, in modo che sia più facile da trovare quando è necessario.</span><span class="sxs-lookup"><span data-stu-id="9e829-114">You can name it HLSharedProjectMainPart4.unity so it's easier to find when you need it.</span></span>

2. <span data-ttu-id="9e829-115">Dalla finestra del progetto, nella cartella Asset-> Scripts, fare doppio clic su GenericNetSync per aprirlo in Visual Studio o in quello che si sta usando.</span><span class="sxs-lookup"><span data-stu-id="9e829-115">From the Project window, in the Assets->Scripts folder, double-click GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="9e829-117">Nelle righe 34 e 38 rimuovere "//" per attivare il codice per la tabella che verrà utilizzata in questa lezione.</span><span class="sxs-lookup"><span data-stu-id="9e829-117">On Lines 34 and 38, remove "//" to activate the code for the table that you will use in this lesson.</span></span> <span data-ttu-id="9e829-118">Salvare quindi il file.</span><span class="sxs-lookup"><span data-stu-id="9e829-118">Next, save the file.</span></span> 

![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="9e829-120">Nella finestra del progetto fare doppio clic sul file PhotonRoom.cs nella cartella assets-> Scripts per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9e829-120">In the Project window, double-click the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span> 

![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="9e829-122">Proprio come nel passaggio 3, è necessario rimuovere "//" per attivare il codice alle righe 25, 26 e 106.</span><span class="sxs-lookup"><span data-stu-id="9e829-122">Just like in Step 3, we need to remove "//" to activate the code at Lines 25, 26, and 106.</span></span>

![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png) 

![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="9e829-125">Nella visualizzazione gerarchia selezionare l'oggetto NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="9e829-125">In the Hierarchy view, select the NetworkRoom object.</span></span>

![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="9e829-127">Nella visualizzazione del progetto passare a assets-> Resources-> prefabbricates.</span><span class="sxs-lookup"><span data-stu-id="9e829-127">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="9e829-128">Prima di tutto, trascinare e rilasciare la tabella prefabbricata nello slot Tableprefab della classe PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="9e829-128">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="9e829-129">Trascinare quindi il RocketLauncherCompleteVariantprefab nello slot prefabbricato del modulo nella classe PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="9e829-129">Next, drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

<span data-ttu-id="9e829-131">Nota: se si fa clic su uno degli oggetti prefabbricati e sulla versione, il controllo passerà a tale oggetto.</span><span class="sxs-lookup"><span data-stu-id="9e829-131">Note: If you click one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="9e829-132">Fare clic, trascinare, rilasciare e rilasciare ogni oggetto nello slot appropriato.</span><span class="sxs-lookup"><span data-stu-id="9e829-132">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="9e829-133">Fare clic sulla freccia a sinistra di MixedRealityPlayspace e spostare l'oggetto gioco figlio MainCamera nella precostruzione SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="9e829-133">Click the arrow to the left of MixedRealityPlayspace and move the child game object MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="9e829-134">Successivamente, eliminare il prefabbricato, MixedRealityPlayspace selezionando la prefabbricata e toccare "Delete" sulla tastiera.</span><span class="sxs-lookup"><span data-stu-id="9e829-134">Next, delete the prefab, MixedRealityPlayspace by selecting the prefab and tap "delete" on your keyboard).</span></span>
<span data-ttu-id="9e829-135">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span><span class="sxs-lookup"><span data-stu-id="9e829-135">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span></span>

><span data-ttu-id="9e829-136">Nota: assicurarsi che le posizioni della fotocamera principale e del SharedPlayground siano impostate su 0, 0, 0.</span><span class="sxs-lookup"><span data-stu-id="9e829-136">Note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>
>

9. <span data-ttu-id="9e829-137">Creare un nuovo set di oggetti di gioco come oggetto figlio per l'oggetto padre SharedPlayground per creare un nuovo oggetto.</span><span class="sxs-lookup"><span data-stu-id="9e829-137">Create a new game object set as a child object to the SharedPlayground parent object to create a new object.</span></span> <span data-ttu-id="9e829-138">Fare clic con il pulsante destro del mouse sull'oggetto padre e scegliere Crea vuoto.</span><span class="sxs-lookup"><span data-stu-id="9e829-138">Right-click the parent object and select Create Empty.</span></span> 

10. <span data-ttu-id="9e829-139">Con il nuovo oggetto selezionato nella gerarchia, modificare il nome dell'oggetto in TableAnchor nel pannello Inspector.</span><span class="sxs-lookup"><span data-stu-id="9e829-139">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="9e829-140">Inoltre, fare clic su Aggiungi componente e cercare il componente TableAnchor.</span><span class="sxs-lookup"><span data-stu-id="9e829-140">Also, click Add Component and search for the TableAnchor component.</span></span> <span data-ttu-id="9e829-141">Selezionarlo e aggiungerlo all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="9e829-141">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="9e829-143">Dal pannello progetto nella cartella prefabbricati trascinare la tabella prefabbricata nell'oggetto figlio "TableAnchor" appena creato.</span><span class="sxs-lookup"><span data-stu-id="9e829-143">From the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object that you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

12. <span data-ttu-id="9e829-145">Nell'oggetto DebugWindow, impostare la larghezza su 50 e l'altezza su 20.</span><span class="sxs-lookup"><span data-stu-id="9e829-145">In the DebugWindow object, change the width to 50 and the height to 20.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)

## <a name="congratulations"></a><span data-ttu-id="9e829-147">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="9e829-147">Congratulations</span></span>


<span data-ttu-id="9e829-148">Al termine di questa operazione, tutti gli utenti che partecipano al progetto Unity possono spostare l'avvio Lunar.</span><span class="sxs-lookup"><span data-stu-id="9e829-148">Once this is complete, all users that join your Unity project can move the lunar launcher around.</span></span> <span data-ttu-id="9e829-149">Tutti i movimenti sono sincronizzati in modo che ogni utente possa visualizzare le interazioni di ogni altro utente.</span><span class="sxs-lookup"><span data-stu-id="9e829-149">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="9e829-150">Questi concetti servono come blocchi predefiniti fondamentali per esperienze di collaborazione condivise complete.</span><span class="sxs-lookup"><span data-stu-id="9e829-150">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span> 

<span data-ttu-id="9e829-151">Sebbene tutti gli utenti siano connessi come parte di un'esperienza condivisa e possano visualizzare i movimenti relativi degli oggetti, l'applicazione non è ancora in grado di allineare in modo accurato gli avatar e gli oggetti in modo che gli utenti locali vedano reciprocamente gli oggetti e nella stessa posizione all'interno del computer fisico mondo.</span><span class="sxs-lookup"><span data-stu-id="9e829-151">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="9e829-152">Per ancorare un'esperienza condivisa locale, ogni dispositivo richiede una conoscenza comune dell'ambiente fisico.</span><span class="sxs-lookup"><span data-stu-id="9e829-152">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="9e829-153">In questo modulo questa operazione verrà eseguita usando gli [ancoraggi spaziali di Azure](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) che saranno implementati nella lezione successiva.</span><span class="sxs-lookup"><span data-stu-id="9e829-153">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) which will be implemented in the next lesson.</span></span>

<span data-ttu-id="9e829-154">Prima di procedere alla lezione successiva, è necessario completare il modulo di apprendimento ASA che copre le nozioni di base di ASA, la creazione di account e risorse di Azure, nonché altri blocchi fondamentali dell'edificio necessari prima di poter integrare questa funzionalità nell'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="9e829-154">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, as well as other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="9e829-155">[Lezione successiva: 5. integrazione degli ancoraggi spaziali di Azure in un'esperienza condivisa](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="9e829-155">[Next Lesson: 5. Integration Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch5.md)</span></span>


---
title: Esercitazioni sulle funzionalità multiutente - 4. Condivisione dei movimenti di oggetti con più utenti
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: b0ddf0799fd94c29ce8f1221c55073cd77b63703
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031252"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="775ba-105">4. Condivisione dei movimenti di oggetti con più utenti</span><span class="sxs-lookup"><span data-stu-id="775ba-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="775ba-106">In questa esercitazione imparerai a condividere i movimenti degli oggetti in modo che tutti i partecipanti di una sessione condivisa possano collaborare e visualizzare le interazioni reciproche.</span><span class="sxs-lookup"><span data-stu-id="775ba-106">In this Tutorial, you'll learn how to share the movements of objects so that all participants of a shared session can collaborate and view each others' interactions.</span></span> <span data-ttu-id="775ba-107">Questa lezione si basa sull'uso del modulo lunare creato durante le [esercitazioni relative al modulo di base](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="775ba-107">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

## <a name="objectives"></a><span data-ttu-id="775ba-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="775ba-108">Objectives</span></span>

- <span data-ttu-id="775ba-109">Introdurre il modulo lunare come modello 3D da condividere</span><span class="sxs-lookup"><span data-stu-id="775ba-109">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="775ba-110">Configurare il progetto per condividere i movimenti del modello 3D</span><span class="sxs-lookup"><span data-stu-id="775ba-110">Configure your project to share the movements of the 3D model</span></span>
- <span data-ttu-id="775ba-111">Imparare a creare un'applicazione collaborativa multiutente di base</span><span class="sxs-lookup"><span data-stu-id="775ba-111">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="instructions"></a><span data-ttu-id="775ba-112">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="775ba-112">Instructions</span></span>

1. <span data-ttu-id="775ba-113">Salva la scena della lezione precedente (CTRL+S).</span><span class="sxs-lookup"><span data-stu-id="775ba-113">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="775ba-114">Puoi denominarla HLSharedProjectMainPart4.unity per poterla trovare più facilmente in caso di necessità.</span><span class="sxs-lookup"><span data-stu-id="775ba-114">You can name it HLSharedProjectMainPart4.unity so it's easier to find when you need it.</span></span>

2. <span data-ttu-id="775ba-115">Nella finestra Project (Progetto), nella cartella Assets->Scripts (Asset->Script), fai doppio clic su GenericNetSync per aprirlo in Visual Studio o in qualsiasi editor di codice in uso.</span><span class="sxs-lookup"><span data-stu-id="775ba-115">From the Project window, in the Assets->Scripts folder, double-click GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="775ba-117">Nelle righe 34 e 38 rimuovi "//" per attivare il codice della tabella che userai in questa lezione.</span><span class="sxs-lookup"><span data-stu-id="775ba-117">On Lines 34 and 38, remove "//" to activate the code for the table that you will use in this lesson.</span></span> <span data-ttu-id="775ba-118">Salva quindi il file.</span><span class="sxs-lookup"><span data-stu-id="775ba-118">Next, save the file.</span></span>

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="775ba-120">Nella finestra Project (Progetto) fai doppio clic sul file PhotonRoom.cs nella cartella Assets->Scripts (Asset->Script) per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="775ba-120">In the Project window, double-click the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span>

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="775ba-122">Come nel passaggio 3, dobbiamo rimuovere "//" per attivare il codice nelle righe 25, 26 e 106.</span><span class="sxs-lookup"><span data-stu-id="775ba-122">Just like in Step 3, we need to remove "//" to activate the code at Lines 25, 26, and 106.</span></span>

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="775ba-125">Nella visualizzazione Hierarchy (Gerarchia) seleziona l'oggetto NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="775ba-125">In the Hierarchy view, select the NetworkRoom object.</span></span>

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="775ba-127">Nella visualizzazione Project (Progetto) passa ad Assets->Resources->Prefabs (Asset->Risorse->Prefab).</span><span class="sxs-lookup"><span data-stu-id="775ba-127">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="775ba-128">Trascina prima il prefab Table nello slot Tableprefab della classe PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="775ba-128">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="775ba-129">Trascina quindi RocketLauncherCompleteVariantprefab nello slot Module Prefab della classe PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="775ba-129">Next, drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    ><span data-ttu-id="775ba-131">Se fai clic su uno degli oggetti prefab e lo rilasci, in Inspector (Controllo) verrà visualizzato tale oggetto.</span><span class="sxs-lookup"><span data-stu-id="775ba-131">If you click one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="775ba-132">Fai clic, trascina e rilascia ogni oggetto nello slot appropriato.</span><span class="sxs-lookup"><span data-stu-id="775ba-132">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="775ba-133">Fai clic sulla freccia a sinistra di MixedRealityPlayspace e sposta l'oggetto gioco figlio MainCamera in basso nel prefab SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="775ba-133">Click the arrow to the left of MixedRealityPlayspace and move the child game object MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="775ba-134">Successivamente, elimina il prefab MixedRealityPlayspace selezionandolo e toccando "CANC" sulla tastiera.</span><span class="sxs-lookup"><span data-stu-id="775ba-134">Next, delete the prefab, MixedRealityPlayspace by selecting the prefab and tap "delete" on your keyboard).</span></span>

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    ><span data-ttu-id="775ba-136">Verifica che le posizioni di MainCamera e SharedPlayground siano entrambe impostate su 0,0,0.</span><span class="sxs-lookup"><span data-stu-id="775ba-136">Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="775ba-137">Seleziona l'oggetto "SharedPlayground" e fai clic con il pulsante destro del mouse per scegliere l'opzione "Create Empty" (Crea vuoto) e creare un oggetto gioco vuoto come figlio dell'oggetto gioco "SharedPlayground".</span><span class="sxs-lookup"><span data-stu-id="775ba-137">Select "SharedPlayground" object and right click the mouse to choose "create empty" option to create an empty game object as a child of "SharedPlayground" game object.</span></span>

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. <span data-ttu-id="775ba-139">Con il nuovo oggetto selezionato nella gerarchia, modifica il nome dell'oggetto in TableAnchor nel riquadro Inspector (Controllo).</span><span class="sxs-lookup"><span data-stu-id="775ba-139">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="775ba-140">Inoltre, fai clic su Add Component (Aggiungi componente) e cerca il componente TableAnchor.</span><span class="sxs-lookup"><span data-stu-id="775ba-140">Also, click Add Component and search for the TableAnchor component.</span></span> <span data-ttu-id="775ba-141">Selezionalo e aggiungilo all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="775ba-141">Select it and add it to the object.</span></span>

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="775ba-143">Nel riquadro Project (Progetto) della cartella Prefabs (Prefab) trascina il prefab Table nell'oggetto figlio "TableAnchor" appena creato.</span><span class="sxs-lookup"><span data-stu-id="775ba-143">From the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object that you just created.</span></span>

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

## <a name="congratulations"></a><span data-ttu-id="775ba-145">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="775ba-145">Congratulations</span></span>

<span data-ttu-id="775ba-146">Al termine, cerca il modulo lunare.</span><span class="sxs-lookup"><span data-stu-id="775ba-146">Once this is complete, look around to find the lunar module.</span></span> <span data-ttu-id="775ba-147">Successivamente, tutti gli utenti che partecipano al progetto Unity potranno spostare il modulo lunare.</span><span class="sxs-lookup"><span data-stu-id="775ba-147">After this, all users that join your Unity project can move the lunar launcher around.</span></span>  <span data-ttu-id="775ba-148">Tutti i movimenti vengono sincronizzati in modo che ogni utente possa vedere le interazioni reciproche.</span><span class="sxs-lookup"><span data-stu-id="775ba-148">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="775ba-149">Questi concetti costituiscono i blocchi predefiniti fondamentali per esperienze di collaborazione complete e condivise.</span><span class="sxs-lookup"><span data-stu-id="775ba-149">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span>

<span data-ttu-id="775ba-150">Anche se tutti gli utenti sono connessi nell'ambito di un'esperienza condivisa e possono vedere i movimenti relativi degli oggetti, l'applicazione non è ancora in grado di allineare in modo preciso avatar e oggetti, tanto che gli utenti locali non sono in grado di vedersi e di vedere gli oggetti nella stessa posizione all'interno del mondo fisico.</span><span class="sxs-lookup"><span data-stu-id="775ba-150">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users were not able see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="775ba-151">Per ancorare un'esperienza condivisa locale, tutti i dispositivi devono avere una comune comprensione dell'ambiente fisico.</span><span class="sxs-lookup"><span data-stu-id="775ba-151">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="775ba-152">A questo scopo, in questo modulo useremo [Ancoraggi nello spazio di Azure](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) che verrà implementato nella prossima lezione.</span><span class="sxs-lookup"><span data-stu-id="775ba-152">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) which will be implemented in the next lesson.</span></span>

<span data-ttu-id="775ba-153">Prima di procedere con la prossima lezione, dobbiamo completare il modulo di apprendimento di ASA, che comprende le nozioni di base di ASA, la creazione di risorse e account di Azure, nonché altri blocchi predefiniti fondamentali, necessari per l'integrazione nell'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="775ba-153">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, as well as other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="775ba-154">[Lezione successiva: 5. Integrazione di Ancoraggi nello spazio di Azure in un'esperienza condivisa](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="775ba-154">[Next Lesson: 5. Integration Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch5.md)</span></span>

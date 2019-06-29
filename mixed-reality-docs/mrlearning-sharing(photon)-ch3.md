---
title: MR Learning condivisione del modulo per HoloLens 2
description: Completare questo corso di informazioni su come implementare esperienze condivise con più utenti all'interno di un'applicazione 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 4625acfcb3353e9537961a444012452139705359
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465211"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="fdee5-104">**Ci si connette più utenti**</span><span class="sxs-lookup"><span data-stu-id="fdee5-104">**Connecting multiple users**</span></span> 

<span data-ttu-id="fdee5-105">In questa lezione, è informazioni su come connettere più utenti come parte di una condividere esperienze in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="fdee5-105">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="fdee5-106">Al termine di questa lezione, sarà in grado di aprire l'applicazione in più dispositivi e vedere avatar, rappresentato da una sfera, le rappresentazioni di ogni persona che unisce in join.</span><span class="sxs-lookup"><span data-stu-id="fdee5-106">By the end of this lesson, you'll be able to open the application on multiple devices, and see avatar, represented by a sphere, representations of each person that joins.</span></span> 

<span data-ttu-id="fdee5-107">Obiettivi:</span><span class="sxs-lookup"><span data-stu-id="fdee5-107">Objectives:</span></span>

- <span data-ttu-id="fdee5-108">Configurare il gioco di parole all'interno dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="fdee5-108">Configure PUN within your application</span></span>
- <span data-ttu-id="fdee5-109">Configurare i lettori</span><span class="sxs-lookup"><span data-stu-id="fdee5-109">Configure players</span></span>
- <span data-ttu-id="fdee5-110">Informazioni su come connettere più utenti un'esperienza condiviso</span><span class="sxs-lookup"><span data-stu-id="fdee5-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="fdee5-111">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="fdee5-111">Instructions</span></span>

1. <span data-ttu-id="fdee5-112">Negli asset -> risorse -> cartella Prefabs nel Pannello di progetto selezionare e trascinare il prefab NetworkLobby in per la gerarchia come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="fdee5-112">In the Assets->Resources->Prefabs folder in the Project panel, drag and drop the NetworkLobby prefab in to the hierarchy as shown in the image below.</span></span>


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="fdee5-114">Quando si espande NetworkLobby, si noterà un oggetto figlio denominato NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="fdee5-114">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="fdee5-115">Con NetworkRoom selezionate, passare al pannello di controllo e fare clic su Add Component.</span><span class="sxs-lookup"><span data-stu-id="fdee5-115">With NetworkRoom selected, go into the Inspector panel, and click Add Component.</span></span> <span data-ttu-id="fdee5-116">Cercare PhotonView e aggiungere il componente.</span><span class="sxs-lookup"><span data-stu-id="fdee5-116">Search for PhotonView and add the component.</span></span>

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="fdee5-118">Creare un nuovo oggetto gioco vuoto nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="fdee5-118">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="fdee5-119">Fare clic con il pulsante destro nella gerarchia e seleziona vuoto dal menu di scelta rapida.</span><span class="sxs-lookup"><span data-stu-id="fdee5-119">Right click in the hierarchy, and select Empty from the Context menu.</span></span> <span data-ttu-id="fdee5-120">Verificare che il posizionamento è impostato su x = 0, y = 0, z = 0 e assegnare il nome dell'oggetto, PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="fdee5-120">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="fdee5-122">Fare clic su Add Component e digitare generico sincronizzazione delta. Selezionare la classe generica sincronizzazione delta.</span><span class="sxs-lookup"><span data-stu-id="fdee5-122">Click Add Component, and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="fdee5-123">Quando la classe viene visualizzata, fare clic sulla casella di controllo utente per accenderlo.</span><span class="sxs-lookup"><span data-stu-id="fdee5-123">When the class appears, click on the User check box to turn it on.</span></span> 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="fdee5-125">Fare nuovamente clic su Add Component e digitare Photon View.</span><span class="sxs-lookup"><span data-stu-id="fdee5-125">Click on Add Component again, and type Photon View.</span></span> <span data-ttu-id="fdee5-126">Selezionare la classe di visualizzazione Photon che viene visualizzato nell'elenco a discesa.</span><span class="sxs-lookup"><span data-stu-id="fdee5-126">Select the Photon View class that appears in the drop-down list.</span></span>

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="fdee5-128">Fare clic sull'icona del File per la classe generica sincronizzazione delta.</span><span class="sxs-lookup"><span data-stu-id="fdee5-128">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="fdee5-129">Trascinare e rilasciare il campo osservati i componenti della visualizzazione Photon.</span><span class="sxs-lookup"><span data-stu-id="fdee5-129">Drag and drop it in the Photon View's Observed Components field.</span></span> ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="fdee5-131">Quindi, creiamo sfere per rappresentare ogni persona che unisce in join un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="fdee5-131">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="fdee5-132">L'oggetto PhotonUser appena creato e scrolldown a con il pulsante destro fare clic su "oggetto 3D e scegliere sfera.</span><span class="sxs-lookup"><span data-stu-id="fdee5-132">Right click the PhotonUser object you just created, and scrolldown to "3D Object, and click Sphere.</span></span> <span data-ttu-id="fdee5-133">Questo verrà creato un oggetto gioco sfera come elemento figlio dell'oggetto PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="fdee5-133">This will create a sphere game object as a child of the PhotonUser object.</span></span>

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="fdee5-135">Ridimensionare la sfera down x = 0,06, y = 0,06, ad z = 0,06.</span><span class="sxs-lookup"><span data-stu-id="fdee5-135">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="fdee5-137">Trascinare l'oggetto gioco PhotonUser nella cartella Prefabs nel Pannello di progetto e quindi eliminarlo dalla scena.</span><span class="sxs-lookup"><span data-stu-id="fdee5-137">Drag the PhotonUser game object into the Prefabs folder in the Project panel, and then delete it from the scene.</span></span> <span data-ttu-id="fdee5-138">A questo punto sono stati creati un prefab che può essere utilizzato quando durante la generazione o creare un'istanza nuova giocatori un'esperienza condiviso.</span><span class="sxs-lookup"><span data-stu-id="fdee5-138">We have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="fdee5-140">Nota: assicurarsi che l'oggetto gioco ha copiato correttamente nella cartella Prefabs prima di eliminarlo dalla gerarchia.</span><span class="sxs-lookup"><span data-stu-id="fdee5-140">Note: ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="fdee5-141">Creare un nuovo oggetto nella gerarchia, seguendo le istruzioni nel passaggio 3 e denominarlo SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="fdee5-141">Create a new object in the hierarchy by following the instructions in Step 3, and name it SharedPlayground.</span></span> <span data-ttu-id="fdee5-142">Quindi, fare clic su Add Component e cercare il gestore di rete generici e fare clic per aggiungere il componente di gestione di rete generici.</span><span class="sxs-lookup"><span data-stu-id="fdee5-142">Then, click Add Component, and search for generic network manager, and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="fdee5-143">Modificare la posizione dell'oggetto su x = 0, y = 0 e z = 0.</span><span class="sxs-lookup"><span data-stu-id="fdee5-143">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="fdee5-145">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="fdee5-145">Congratulations</span></span>

<span data-ttu-id="fdee5-146">Dopo che tutti i passaggi precedenti sono stati completati e il processo di compilazione è completo, fare clic sul pulsante play e connettersi i 2 HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fdee5-146">Once all the steps above are complete, and the build process is also complete, press the play button and connect your HoloLens 2.</span></span> <span data-ttu-id="fdee5-147">Verrà visualizzata una sfera muove quando si sposta la testa.</span><span class="sxs-lookup"><span data-stu-id="fdee5-147">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="fdee5-148">Questa informazione verrà visualizzata per tutti gli utenti che unisce in join di un progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="fdee5-148">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="fdee5-149">[Lezione successiva: Sharing(photon) lezione 4](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="fdee5-149">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>


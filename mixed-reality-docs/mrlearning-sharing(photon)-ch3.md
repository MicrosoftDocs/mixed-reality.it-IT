---
title: MR Learning condivisione del modulo per HoloLens 2
description: Completare questo corso di informazioni su come implementare esperienze condivise con più utenti all'interno di un'applicazione 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 33f265c6333f12f7ec73ecb0c1e5730b168d4bde
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415912"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="026df-104">**Ci si connette più utenti**</span><span class="sxs-lookup"><span data-stu-id="026df-104">**Connecting Multiple Users**</span></span> 

<span data-ttu-id="026df-105">In questa lezione si apprenderà come connettersi a più utenti come parte di una condividere esperienze in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="026df-105">In this lesson, we will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="026df-106">Al termine di questa lezione, sarà in grado di aprire l'applicazione in più dispositivi e visualizzare rappresentazioni "avatar" di ogni persona che unisce in join (avatar rappresentato da una sfera).</span><span class="sxs-lookup"><span data-stu-id="026df-106">By the end of this lesson, you will be able to open the application on multiple devices, and see "avatar" representations of each person that joins (avatars represented by a sphere.)</span></span> 

<span data-ttu-id="026df-107">Obiettivi:</span><span class="sxs-lookup"><span data-stu-id="026df-107">Objectives:</span></span>

- <span data-ttu-id="026df-108">Configurare il gioco di parole all'interno dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="026df-108">Configure PUN within your application</span></span>
- <span data-ttu-id="026df-109">Configurare i lettori</span><span class="sxs-lookup"><span data-stu-id="026df-109">Configure players</span></span>
- <span data-ttu-id="026df-110">Informazioni su come connettere più utenti un'esperienza condiviso</span><span class="sxs-lookup"><span data-stu-id="026df-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="026df-111">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="026df-111">Instructions</span></span>

1. <span data-ttu-id="026df-112">Negli asset > risorse > Prefabs cartella del pannello progetto, trascinamento e rilascio "NetworkLobby" prefab alla gerarchia, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="026df-112">In the Assets>Resources>Prefabs folder of the project panel, drag and drop the "NetworkLobby" prefab in to the hierarchy, as shown in the image below.</span></span>


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="026df-114">Quando si espande il prefab "NetworkLobby", verrà visualizzato un oggetto figlio denominato "NetworkRoom."</span><span class="sxs-lookup"><span data-stu-id="026df-114">When you expand the prefab "NetworkLobby," you should see a child object called "NetworkRoom."</span></span> <span data-ttu-id="026df-115">Con essa selezionate, passare al pannello di controllo e fare clic su "Aggiungi componente".</span><span class="sxs-lookup"><span data-stu-id="026df-115">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="026df-116">Cercare "PhotonView" e aggiungere il componente.</span><span class="sxs-lookup"><span data-stu-id="026df-116">Search for "PhotonView" and add the component.</span></span>

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="026df-118">Creare un nuovo oggetto gioco vuoto nella gerarchia (fare clic con il pulsante destro nella gerarchia e selezionare "Vuoto" dal menu di scelta rapida).</span><span class="sxs-lookup"><span data-stu-id="026df-118">Create a new empty game object in the hierarchy (right click in the hierarchy and select "Empty" from the context menu).</span></span> <span data-ttu-id="026df-119">Verificare che il posizionamento è impostato su x = 0, y = 0, z = 0 e assegnare il nome dell'oggetto, "PhotonUser."</span><span class="sxs-lookup"><span data-stu-id="026df-119">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="026df-121">Fare clic sul pulsante "Add Component" e digitare "Sync Net generica" e selezionare la classe generica sincronizzazione delta.</span><span class="sxs-lookup"><span data-stu-id="026df-121">Click on the "Add Component" button and type "Generic Net Sync" and select the Generic Net Sync class.</span></span> <span data-ttu-id="026df-122">Dopo che la classe viene visualizzata, fare clic nella casella di controllo "User" per accenderlo.</span><span class="sxs-lookup"><span data-stu-id="026df-122">Once the class appears, click on the "User" check box to turn it on.</span></span> 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="026df-124">Anche in questo caso fare clic su "Add Component" e quindi digitare "Photon visualizzazione" e selezionare la classe di visualizzazione Photon che viene visualizzato nell'elenco a discesa.</span><span class="sxs-lookup"><span data-stu-id="026df-124">Again click on "Add Component" and then type "Photon View" and select the Photon View class that appears in the drop down list.</span></span>

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="026df-126">A questo punto fare clic sull'icona del File in per la classe generica sincronizzazione delta, quindi trascinare e rilasciarlo al campo "Componenti osservato" della vista Photon.</span><span class="sxs-lookup"><span data-stu-id="026df-126">Now click on the File icon in for the Generic Net Sync class, then drag and drop it to the Photon View's "Observed Components" field.</span></span> ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="026df-128">Successivamente, si vuole creare sfere per rappresentare ogni persona che unisce in join un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="026df-128">Next, we want to create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="026df-129">Fare clic con il pulsante destro l'oggetto "PhotonUser" appena creato, andare alla "oggetto 3D" e fare clic su "Sfera."</span><span class="sxs-lookup"><span data-stu-id="026df-129">Right click the "PhotonUser" object you just created, go down to "3D Object" and click "Sphere."</span></span> <span data-ttu-id="026df-130">Questo verrà creato un oggetto gioco sfera come elemento figlio dell'oggetto PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="026df-130">This will create a sphere game object as a child of the PhotonUser object.</span></span>

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="026df-132">Ridimensionare la sfera down x = 0,06, y = 0,06, ad z = 0,06.</span><span class="sxs-lookup"><span data-stu-id="026df-132">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="026df-134">Trascinare l'oggetto gioco "PhotonUser" nella cartella "prefabs" nel Pannello di progetto.</span><span class="sxs-lookup"><span data-stu-id="026df-134">Drag the "PhotonUser" game object into the "prefabs" folder in the project panel.</span></span> <span data-ttu-id="026df-135">Quindi, eliminarlo dalla scena.</span><span class="sxs-lookup"><span data-stu-id="026df-135">Then, delete it from the scene.</span></span> <span data-ttu-id="026df-136">A questo punto sono stati creati un prefab che verrà utilizzato quando durante la generazione o creare un'istanza nuova giocatori un'esperienza condiviso.</span><span class="sxs-lookup"><span data-stu-id="026df-136">We have now created a prefab that will be used when spawning or instantiating new players in a shared experience.</span></span>

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="026df-138">Nota: assicurarsi che l'oggetto gioco ha copiato correttamente nella cartella "prefabs" prima di eliminarlo dalla gerarchia.</span><span class="sxs-lookup"><span data-stu-id="026df-138">Note: ensure that the game object has successfully copied into the "prefabs" folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="026df-139">Creare un nuovo oggetto della gerarchia (con istruzioni simili a quello del passaggio 3) e denominarlo "SharedPlayground."</span><span class="sxs-lookup"><span data-stu-id="026df-139">Create a new object in the hierarchy (using similar instructions to that of Step 3), and name it "SharedPlayground."</span></span> <span data-ttu-id="026df-140">Quindi, fare clic su "Add Component" e cercare "gestione di rete generica" e fare clic per aggiungere il componente di gestione di rete generico.</span><span class="sxs-lookup"><span data-stu-id="026df-140">Then, click "Add Component" and search for "generic network manager" and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="026df-141">Modificare la posizione dell'oggetto su x = 0, y = 0 e z = 0.</span><span class="sxs-lookup"><span data-stu-id="026df-141">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="026df-143">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="026df-143">Congratulations</span></span>

<span data-ttu-id="026df-144">Dopo tutti i passaggi precedenti sono stati completati e il processo di compilazione è completo, quando si preme il pulsante di riproduzione e connette la 2 HoloLens, viene visualizzata una sfera muove quando si sposta la testa.</span><span class="sxs-lookup"><span data-stu-id="026df-144">Once all the steps above are complete, and the build process is complete, when you press the play button and connect your HoloLens 2, you should see a sphere moving around as you move your head!</span></span> <span data-ttu-id="026df-145">Questa informazione verrà visualizzata per tutti gli utenti che unisce in join di un progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="026df-145">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="026df-146">[Lezione successiva: Sharing(photon) lezione 4](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="026df-146">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>


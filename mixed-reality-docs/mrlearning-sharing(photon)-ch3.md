---
title: MR Learning condivisione del modulo per HoloLens 2
description: Completare questo corso di informazioni su come implementare esperienze condivise con più utenti all'interno di un'applicazione 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: f2e8cef618ea2fbee398ce19f1ba60b712b5fe3e
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327444"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="fa62d-104">**Ci si connette più utenti**</span><span class="sxs-lookup"><span data-stu-id="fa62d-104">**Connecting Multiple Users**</span></span> 

<span data-ttu-id="fa62d-105">In questa lezione si apprenderà come connettersi a più utenti come parte di una condividere esperienze in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="fa62d-105">In this lesson, we will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="fa62d-106">Al termine di questa lezione, sarà in grado di aprire l'applicazione in più dispositivi e visualizzare rappresentazioni "avatar" di ogni persona che unisce in join (avatar rappresentato da una sfera).</span><span class="sxs-lookup"><span data-stu-id="fa62d-106">By the end of this lesson, you will be able to open the application on multiple devices, and see "avatar" representations of each person that joins (avatars represented by a sphere.)</span></span> 

<span data-ttu-id="fa62d-107">Obiettivi:</span><span class="sxs-lookup"><span data-stu-id="fa62d-107">Objectives:</span></span>

- <span data-ttu-id="fa62d-108">Configurare il gioco di parole all'interno dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="fa62d-108">Configure PUN within your application</span></span>
- <span data-ttu-id="fa62d-109">Configurare i lettori</span><span class="sxs-lookup"><span data-stu-id="fa62d-109">Configure players</span></span>
- <span data-ttu-id="fa62d-110">Informazioni su come connettere più utenti un'esperienza condiviso</span><span class="sxs-lookup"><span data-stu-id="fa62d-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="fa62d-111">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="fa62d-111">Instructions</span></span>

1. <span data-ttu-id="fa62d-112">Negli asset > risorse > Prefabs cartella del pannello progetto, trascinamento e rilascio "NetworkLobby" prefab alla gerarchia, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="fa62d-112">In the Assets>Resources>Prefabs folder of the project panel, drag and drop the "NetworkLobby" prefab in to the hierarchy, as shown in the image below.</span></span>


![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="fa62d-114">Quando si espande il prefab "NetworkLobby", verrà visualizzato un oggetto figlio denominato "NetworkRoom."</span><span class="sxs-lookup"><span data-stu-id="fa62d-114">When you expand the prefab "NetworkLobby," you should see a child object called "NetworkRoom."</span></span> <span data-ttu-id="fa62d-115">Con essa selezionate, passare al pannello di controllo e fare clic su "Aggiungi componente".</span><span class="sxs-lookup"><span data-stu-id="fa62d-115">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="fa62d-116">Cercare "PhotonView" e aggiungere il componente.</span><span class="sxs-lookup"><span data-stu-id="fa62d-116">Search for "PhotonView" and add the component.</span></span>

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="fa62d-118">Creare un nuovo oggetto gioco vuoto nella gerarchia (fare clic con il pulsante destro nella gerarchia e selezionare "Vuoto" dal menu di scelta rapida).</span><span class="sxs-lookup"><span data-stu-id="fa62d-118">Create a new empty game object in the hierarchy (right click in the hierarchy and select "Empty" from the context menu).</span></span> <span data-ttu-id="fa62d-119">Verificare che il posizionamento è impostato su x = 0, y = 0, z = 0 e assegnare il nome dell'oggetto, "PhotonUser."</span><span class="sxs-lookup"><span data-stu-id="fa62d-119">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="fa62d-121">Successivamente, si vuole creare sfere per rappresentare ogni persona che unisce in join un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="fa62d-121">Next, we want to create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="fa62d-122">Fare clic con il pulsante destro l'oggetto "PhotonUser" appena creato, andare alla "oggetto 3D" e fare clic su "Sfera."</span><span class="sxs-lookup"><span data-stu-id="fa62d-122">Right click the "PhotonUser" object you just created, go down to "3D Object" and click "Sphere."</span></span> <span data-ttu-id="fa62d-123">Questo verrà creato un oggetto gioco sfera come elemento figlio dell'oggetto PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="fa62d-123">This will create a sphere game object as a child of the PhotonUser object.</span></span>

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

5. <span data-ttu-id="fa62d-125">Ridimensionare la sfera down x = 0,06, y = 0,06, ad z = 0,06.</span><span class="sxs-lookup"><span data-stu-id="fa62d-125">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

6. <span data-ttu-id="fa62d-127">Trascinare l'oggetto gioco "PhotonUser" nella cartella "prefabs" nel Pannello di progetto.</span><span class="sxs-lookup"><span data-stu-id="fa62d-127">Drag the "PhotonUser" game object into the "prefabs" folder in the project panel.</span></span> <span data-ttu-id="fa62d-128">Quindi, eliminarlo dalla scena.</span><span class="sxs-lookup"><span data-stu-id="fa62d-128">Then, delete it from the scene.</span></span> <span data-ttu-id="fa62d-129">A questo punto sono stati creati un prefab che verrà utilizzato quando durante la generazione o creare un'istanza nuova giocatori un'esperienza condiviso.</span><span class="sxs-lookup"><span data-stu-id="fa62d-129">We have now created a prefab that will be used when spawning or instantiating new players in a shared experience.</span></span>

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="fa62d-131">Nota: assicurarsi che l'oggetto gioco ha copiato correttamente nella cartella "prefabs" prima di eliminarlo dalla gerarchia.</span><span class="sxs-lookup"><span data-stu-id="fa62d-131">Note: ensure that the game object has successfully copied into the "prefabs" folder before deleting it from your hierarchy.</span></span>

7. <span data-ttu-id="fa62d-132">Creare un nuovo oggetto della gerarchia (con istruzioni simili a quello del passaggio 3) e denominarlo "SharedPlayground."</span><span class="sxs-lookup"><span data-stu-id="fa62d-132">Create a new object in the hierarchy (using similar instructions to that of Step 3), and name it "SharedPlayground."</span></span> <span data-ttu-id="fa62d-133">Quindi, fare clic su "Add Component" e cercare "gestione di rete generica" e fare clic per aggiungere il componente di gestione di rete generico.</span><span class="sxs-lookup"><span data-stu-id="fa62d-133">Then, click "Add Component" and search for "generic network manager" and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="fa62d-134">Modificare la posizione dell'oggetto su x = 0, y = 0 e z = 0.</span><span class="sxs-lookup"><span data-stu-id="fa62d-134">Change the position of the object to x=0, y=0, and z =0.</span></span>

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="fa62d-136">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="fa62d-136">Congratulations</span></span>

<span data-ttu-id="fa62d-137">Dopo tutti i passaggi precedenti sono stati completati e il processo di compilazione è completo, quando si preme il pulsante di riproduzione e connette la 2 HoloLens, viene visualizzata una sfera muove quando si sposta la testa.</span><span class="sxs-lookup"><span data-stu-id="fa62d-137">Once all the steps above are complete, and the build process is complete, when you press the play button and connect your HoloLens 2, you should see a sphere moving around as you move your head!</span></span> <span data-ttu-id="fa62d-138">Questa informazione verrà visualizzata per tutti gli utenti che unisce in join di un progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="fa62d-138">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="fa62d-139">[Lezione successiva: Sharing(photon) lezione 4](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="fa62d-139">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>


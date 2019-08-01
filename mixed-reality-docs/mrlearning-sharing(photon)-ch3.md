---
title: Esercitazioni sulle funzionalità multiutente-3. Connessione di più utenti
description: Completare questo corso per apprendere come implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: d3068a1ebbbc2b6db8b563be8bf8c6e488e9491a
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701935"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="e4660-105">3. Connessione di più utenti</span><span class="sxs-lookup"><span data-stu-id="e4660-105">3. Connecting multiple users</span></span>

<span data-ttu-id="e4660-106">In questa lezione verrà illustrato come connettere più utenti nell'ambito di un'esperienza condivisa Live.</span><span class="sxs-lookup"><span data-stu-id="e4660-106">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="e4660-107">Al termine di questa lezione sarà possibile aprire l'applicazione su più dispositivi e visualizzare avatar, rappresentati da una sfera, rappresentazioni di ogni persona che si unisce.</span><span class="sxs-lookup"><span data-stu-id="e4660-107">By the end of this lesson, you'll be able to open the application on multiple devices, and see avatar, represented by a sphere, representations of each person that joins.</span></span> 

<span data-ttu-id="e4660-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="e4660-108">Objectives:</span></span>

- <span data-ttu-id="e4660-109">Configurare il PUN all'interno dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="e4660-109">Configure PUN within your application</span></span>
- <span data-ttu-id="e4660-110">Configurare i giocatori</span><span class="sxs-lookup"><span data-stu-id="e4660-110">Configure players</span></span>
- <span data-ttu-id="e4660-111">Informazioni su come connettere più utenti in un'esperienza condivisa</span><span class="sxs-lookup"><span data-stu-id="e4660-111">Learn how to connect multiple users in a shared experience</span></span>

## <a name="instructions"></a><span data-ttu-id="e4660-112">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="e4660-112">Instructions</span></span>

1. <span data-ttu-id="e4660-113">Nella cartella Asset-> Resources-> prefabbricates nel pannello del progetto, trascinare il prefabbricato NetworkLobby nella gerarchia, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="e4660-113">In the Assets->Resources->Prefabs folder in the Project panel, drag and drop the NetworkLobby prefab in to the hierarchy as shown in the image below.</span></span>

![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="e4660-115">Quando si espande NetworkLobby, viene visualizzato un oggetto figlio denominato NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="e4660-115">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="e4660-116">Con NetworkRoom selezionato, passare al pannello Inspector e fare clic su Add Component.</span><span class="sxs-lookup"><span data-stu-id="e4660-116">With NetworkRoom selected, go into the Inspector panel, and click Add Component.</span></span> <span data-ttu-id="e4660-117">Cercare PhotonView e aggiungere il componente.</span><span class="sxs-lookup"><span data-stu-id="e4660-117">Search for PhotonView and add the component.</span></span>

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="e4660-119">Creare un nuovo oggetto gioco vuoto nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="e4660-119">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="e4660-120">Fare clic con il pulsante destro del mouse nella gerarchia e scegliere vuota dal menu di scelta rapida.</span><span class="sxs-lookup"><span data-stu-id="e4660-120">Right click in the hierarchy, and select Empty from the Context menu.</span></span> <span data-ttu-id="e4660-121">Verificare che il posizionamento sia impostato su x = 0, y = 0, z = 0 e assegnare un nome all'oggetto, PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="e4660-121">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="e4660-123">Fare clic su Add Component e digitare Generic NET Sync. Selezionare la classe di sincronizzazione NET generica.</span><span class="sxs-lookup"><span data-stu-id="e4660-123">Click Add Component, and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="e4660-124">Quando viene visualizzata la classe, fare clic sulla casella di controllo utente per attivarla.</span><span class="sxs-lookup"><span data-stu-id="e4660-124">When the class appears, click on the User check box to turn it on.</span></span> 

![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="e4660-126">Fare di nuovo clic su Add Component e digitare Photon View.</span><span class="sxs-lookup"><span data-stu-id="e4660-126">Click on Add Component again, and type Photon View.</span></span> <span data-ttu-id="e4660-127">Selezionare la classe di visualizzazione Photon visualizzata nell'elenco a discesa.</span><span class="sxs-lookup"><span data-stu-id="e4660-127">Select the Photon View class that appears in the drop-down list.</span></span>

![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="e4660-129">Fare clic sull'icona file per la classe net Sync generica.</span><span class="sxs-lookup"><span data-stu-id="e4660-129">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="e4660-130">Trascinarla e rilasciarla nel campo componenti osservati della visualizzazione Photon.</span><span class="sxs-lookup"><span data-stu-id="e4660-130">Drag and drop it in the Photon View's Observed Components field.</span></span> 

![module3chapter3updateStep6im. png](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="e4660-132">Si creeranno quindi le sfere per rappresentare ogni persona che partecipa a un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="e4660-132">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="e4660-133">Fare clic con il pulsante destro del mouse sull'oggetto PhotonUser appena creato e ScrollDown su "oggetto 3D e scegliere Sphere.</span><span class="sxs-lookup"><span data-stu-id="e4660-133">Right click the PhotonUser object you just created, and scrolldown to "3D Object, and click Sphere.</span></span> <span data-ttu-id="e4660-134">Verrà creato un oggetto gioco Sphere come figlio dell'oggetto PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="e4660-134">This will create a sphere game object as a child of the PhotonUser object.</span></span>

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="e4660-136">Ridimensionare la sfera fino a x = 0,06, y = 0,06, ad z = 0,06.</span><span class="sxs-lookup"><span data-stu-id="e4660-136">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="e4660-138">Trascinare l'oggetto PhotonUser Game nella cartella prefabbricates nel pannello Project, quindi eliminarlo dalla scena.</span><span class="sxs-lookup"><span data-stu-id="e4660-138">Drag the PhotonUser game object into the Prefabs folder in the Project panel, and then delete it from the scene.</span></span> <span data-ttu-id="e4660-139">A questo punto è stata creata una prefabbricata che può essere usata durante la generazione o la creazione di un'istanza di nuovi giocatori in un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="e4660-139">We have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="e4660-141">Nota: assicurarsi che l'oggetto Game sia stato copiato correttamente nella cartella prefabbricates prima di eliminarlo dalla gerarchia.</span><span class="sxs-lookup"><span data-stu-id="e4660-141">Note: ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="e4660-142">Creare un nuovo oggetto nella gerarchia seguendo le istruzioni riportate nel passaggio 3 e denominarlo SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="e4660-142">Create a new object in the hierarchy by following the instructions in Step 3, and name it SharedPlayground.</span></span> <span data-ttu-id="e4660-143">Quindi, fare clic su Aggiungi componente e cercare gestore reti generico e fare clic su di esso per aggiungere il componente generico di gestione reti.</span><span class="sxs-lookup"><span data-stu-id="e4660-143">Then, click Add Component, and search for generic network manager, and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="e4660-144">Modificare la posizione dell'oggetto in x = 0, y = 0 e z = 0.</span><span class="sxs-lookup"><span data-stu-id="e4660-144">Change the position of the object to x=0, y=0, and z =0.</span></span>

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="e4660-146">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="e4660-146">Congratulations</span></span>

<span data-ttu-id="e4660-147">Una volta completati tutti i passaggi precedenti e il processo di compilazione è stato completato, premere il pulsante Play (Riproduci) e connettere HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e4660-147">Once all the steps above are complete, and the build process is also complete, press the play button and connect your HoloLens 2.</span></span> <span data-ttu-id="e4660-148">Quando si sposta la testa, verrà visualizzata una sfera.</span><span class="sxs-lookup"><span data-stu-id="e4660-148">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="e4660-149">Verrà visualizzato per tutti gli utenti che partecipano al progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="e4660-149">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="e4660-150">[Lezione successiva: 4. Condivisione dei movimenti di oggetti con più utenti](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="e4660-150">[Next Lesson: 4. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch4.md)</span></span>


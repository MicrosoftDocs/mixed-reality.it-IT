---
title: Esercitazioni sulle funzionalità multiutente-3. Connessione di più utenti
description: Completare questo corso per apprendere come implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: a6d1a269f45b4aaf7cbd8fea948ddcbdf0bf18e2
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437740"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="3fc82-105">3. connessione di più utenti</span><span class="sxs-lookup"><span data-stu-id="3fc82-105">3. Connecting multiple users</span></span>

<span data-ttu-id="3fc82-106">In questa lezione verrà illustrato come connettere più utenti nell'ambito di un'esperienza condivisa Live.</span><span class="sxs-lookup"><span data-stu-id="3fc82-106">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="3fc82-107">Al termine di questa lezione sarà possibile aprire l'applicazione su più dispositivi e visualizzare l'avatar, rappresentato da una sfera per ogni persona che si unisce.</span><span class="sxs-lookup"><span data-stu-id="3fc82-107">By the end of this lesson, you'll be able to open the application on multiple devices and see the avatar, represented by a sphere for each person that joins.</span></span> 

<span data-ttu-id="3fc82-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="3fc82-108">Objectives:</span></span>

- <span data-ttu-id="3fc82-109">Configurare il PUN all'interno dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="3fc82-109">Configure PUN within your application</span></span>
- <span data-ttu-id="3fc82-110">Configurare i giocatori</span><span class="sxs-lookup"><span data-stu-id="3fc82-110">Configure players</span></span>
- <span data-ttu-id="3fc82-111">Informazioni su come connettere più utenti in un'esperienza condivisa</span><span class="sxs-lookup"><span data-stu-id="3fc82-111">Learn how to connect multiple users in a shared experience</span></span>

## <a name="instructions"></a><span data-ttu-id="3fc82-112">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="3fc82-112">Instructions</span></span>

1. <span data-ttu-id="3fc82-113">Nella cartella Asset-> Resources-> prefabbricates del pannello del progetto trascinare il NetworkLobby prefabbricato nella gerarchia, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="3fc82-113">In the Assets->Resources->Prefabs folder of the Project panel, drag and drop the NetworkLobby prefab into the hierarchy as shown in the image below.</span></span>

![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="3fc82-115">Quando si espande NetworkLobby, viene visualizzato un oggetto figlio denominato NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="3fc82-115">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="3fc82-116">Con NetworkRoom selezionato, passare al pannello Inspector e fare clic su Add Component.</span><span class="sxs-lookup"><span data-stu-id="3fc82-116">With NetworkRoom selected, go into the Inspector panel and click Add Component.</span></span> <span data-ttu-id="3fc82-117">Cercare PhotonView e aggiungere il componente.</span><span class="sxs-lookup"><span data-stu-id="3fc82-117">Search for PhotonView and add the component.</span></span>

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="3fc82-119">Creare un nuovo oggetto gioco vuoto nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="3fc82-119">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="3fc82-120">Fare clic con il pulsante destro del mouse nella gerarchia e scegliere vuota dal menu di scelta rapida.</span><span class="sxs-lookup"><span data-stu-id="3fc82-120">Right-click in the hierarchy and select Empty from the Context menu.</span></span> <span data-ttu-id="3fc82-121">Verificare che il posizionamento sia impostato su x = 0, y = 0, z = 0 e assegnare un nome all'oggetto, PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="3fc82-121">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="3fc82-123">Fare clic su Add Component e digitare Generic NET Sync. Selezionare la classe di sincronizzazione NET generica.</span><span class="sxs-lookup"><span data-stu-id="3fc82-123">Click Add Component and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="3fc82-124">Quando viene visualizzata la classe, fare clic sulla casella di controllo utente per attivarla.</span><span class="sxs-lookup"><span data-stu-id="3fc82-124">When the class appears, click the User check box to turn it on.</span></span> 

![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="3fc82-126">Fare di nuovo clic su Add Component e digitare Photon View.</span><span class="sxs-lookup"><span data-stu-id="3fc82-126">Click Add Component again, and type Photon View.</span></span> <span data-ttu-id="3fc82-127">Selezionare la classe di visualizzazione Photon visualizzata nell'elenco a discesa.</span><span class="sxs-lookup"><span data-stu-id="3fc82-127">Select the Photon View class that appears in the drop-down list.</span></span>

![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="3fc82-129">Fare clic sull'icona file per la classe net Sync generica.</span><span class="sxs-lookup"><span data-stu-id="3fc82-129">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="3fc82-130">Trascinarla e rilasciarla nel campo componenti osservati della visualizzazione Photon.</span><span class="sxs-lookup"><span data-stu-id="3fc82-130">Drag and drop it in the Photon View's Observed Components field.</span></span> 

![module3chapter3updateStep6im. png](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="3fc82-132">Si creeranno quindi le sfere per rappresentare ogni persona che partecipa a un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="3fc82-132">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="3fc82-133">Fare clic con il pulsante destro del mouse sull'oggetto PhotonUser appena creato, scorrere fino a "oggetto 3D e fare clic su sfera.</span><span class="sxs-lookup"><span data-stu-id="3fc82-133">Right-click the PhotonUser object you just created, scroll-down to "3D Object and click Sphere.</span></span> <span data-ttu-id="3fc82-134">Verrà creato un oggetto gioco Sphere come figlio dell'oggetto PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="3fc82-134">This will create a sphere game object as a child of the PhotonUser object.</span></span>

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="3fc82-136">Ridimensionare la sfera fino a x = 0,06, y = 0,06, ad z = 0,06.</span><span class="sxs-lookup"><span data-stu-id="3fc82-136">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="3fc82-138">Trascinare l'oggetto PhotonUser Game nella cartella prefabbricates nel pannello Project, quindi eliminarlo dalla scena.</span><span class="sxs-lookup"><span data-stu-id="3fc82-138">Drag the PhotonUser game object into the Prefabs folder in the Project panel and then delete it from the scene.</span></span> <span data-ttu-id="3fc82-139">A questo punto è stata creata una prefabbricata che può essere usata durante la generazione o la creazione di un'istanza di nuovi giocatori in un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="3fc82-139">You have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="3fc82-141">Nota: assicurarsi che l'oggetto Game sia stato copiato correttamente nella cartella prefabbricates prima di eliminarlo dalla gerarchia.</span><span class="sxs-lookup"><span data-stu-id="3fc82-141">Note: ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="3fc82-142">Creare un nuovo oggetto nella gerarchia seguendo le istruzioni nel passaggio 3 e denominarlo SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="3fc82-142">Create a new object in the hierarchy by following the instructions in Step 3 and name it SharedPlayground.</span></span> <span data-ttu-id="3fc82-143">Quindi, fare clic su Aggiungi componente e cercare gestore reti generico.</span><span class="sxs-lookup"><span data-stu-id="3fc82-143">Then, click Add Component and search for generic network manager.</span></span>  <span data-ttu-id="3fc82-144">Fare di nuovo clic su di esso per aggiungere il componente generico di gestione reti.</span><span class="sxs-lookup"><span data-stu-id="3fc82-144">Click it again to add the Generic Network Manager component.</span></span> <span data-ttu-id="3fc82-145">Modificare la posizione dell'oggetto in x = 0, y = 0 e z = 0.</span><span class="sxs-lookup"><span data-stu-id="3fc82-145">Change the position of the object to x=0, y=0, and z =0.</span></span>

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="3fc82-147">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="3fc82-147">Congratulations</span></span>

<span data-ttu-id="3fc82-148">Al termine di tutti i passaggi precedenti e del processo di compilazione, premere il pulsante Play (Riproduci) e connettere HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3fc82-148">Once all the steps above are complete and the build process is also complete, press the Play button and connect your HoloLens 2.</span></span> <span data-ttu-id="3fc82-149">Quando si sposta la testa, verrà visualizzata una sfera.</span><span class="sxs-lookup"><span data-stu-id="3fc82-149">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="3fc82-150">Verrà visualizzato per tutti gli utenti che partecipano al progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="3fc82-150">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="3fc82-151">[Lezione successiva: 4. condivisione dei movimenti di oggetti con più utenti](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="3fc82-151">[Next Lesson: 4. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch4.md)</span></span>


---
title: Esercitazioni sulle funzionalità multiutente - 3. Connessione di più utenti
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: cbe0d8d2db6c34ba262fe9c946b68366ed3dbb93
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031223"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="aa03d-105">3. Connessione di più utenti</span><span class="sxs-lookup"><span data-stu-id="aa03d-105">3. Connecting multiple users</span></span>

<span data-ttu-id="aa03d-106">In questa lezione impareremo a connettere più utenti all'interno di un'esperienza live condivisa.</span><span class="sxs-lookup"><span data-stu-id="aa03d-106">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="aa03d-107">Al termine di questa lezione, sarai in grado di aprire l'applicazione in più dispositivi e visualizzare l'avatar, rappresentato da una sfera per ogni persona che partecipa.</span><span class="sxs-lookup"><span data-stu-id="aa03d-107">By the end of this lesson, you'll be able to open the application on multiple devices and see the avatar, represented by a sphere for each person that joins.</span></span>

## <a name="objectives"></a><span data-ttu-id="aa03d-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="aa03d-108">Objectives</span></span>

* <span data-ttu-id="aa03d-109">Configurare PUN all'interno dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="aa03d-109">Configure PUN within your application</span></span>
* <span data-ttu-id="aa03d-110">Configurare i giocatori</span><span class="sxs-lookup"><span data-stu-id="aa03d-110">Configure players</span></span>
* <span data-ttu-id="aa03d-111">Imparare a connettere più utenti in un'esperienza condivisa</span><span class="sxs-lookup"><span data-stu-id="aa03d-111">Learn how to connect multiple users in a shared experience</span></span>

## <a name="instructions"></a><span data-ttu-id="aa03d-112">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="aa03d-112">Instructions</span></span>

1. <span data-ttu-id="aa03d-113">Nella cartella Assets->Resources->Prefabs (Asset->Risorse->Prefab) del riquadro Project (Progetto) trascina il prefab NetworkLobby selezionato nella gerarchia, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="aa03d-113">In the Assets->Resources->Prefabs folder of the Project panel, drag and drop the NetworkLobby prefab into the hierarchy as shown in the image below.</span></span>

    ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="aa03d-115">Quando espandi NetworkLobby, verrà visualizzato un oggetto figlio denominato NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="aa03d-115">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="aa03d-116">Con NetworkRoom selezionato, passa al riquadro Inspector (Controllo) e fai clic su Add Component (Aggiungi componente).</span><span class="sxs-lookup"><span data-stu-id="aa03d-116">With NetworkRoom selected, go into the Inspector panel and click Add Component.</span></span> <span data-ttu-id="aa03d-117">Cerca PhotonView e aggiungi il componente.</span><span class="sxs-lookup"><span data-stu-id="aa03d-117">Search for PhotonView and add the component.</span></span>

    ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="aa03d-119">Crea un nuovo oggetto gioco vuoto nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="aa03d-119">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="aa03d-120">Fai clic con il pulsante destro del mouse nella gerarchia e scegli Empty (Vuoto) dal menu di scelta rapida.</span><span class="sxs-lookup"><span data-stu-id="aa03d-120">Right-click in the hierarchy and select Empty from the Context menu.</span></span> <span data-ttu-id="aa03d-121">Verifica che il posizionamento sia impostato su x = 0, y = 0, z = 0 e assegna all'oggetto il nome PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="aa03d-121">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

    ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="aa03d-123">Fai clic su Add Component (Aggiungi componente) e digita Generic Net Sync. Seleziona la classe Generic Net Sync (Sincronizzazione rete generica).</span><span class="sxs-lookup"><span data-stu-id="aa03d-123">Click Add Component and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="aa03d-124">Quando la classe viene visualizzata, fai clic sulla casella di controllo User (Utente) per attivarla.</span><span class="sxs-lookup"><span data-stu-id="aa03d-124">When the class appears, click the User check box to turn it on.</span></span>

    ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="aa03d-126">Fai di nuovo clic su Add Component (Aggiungi componente) e digita Photon View.</span><span class="sxs-lookup"><span data-stu-id="aa03d-126">Click Add Component again, and type Photon View.</span></span> <span data-ttu-id="aa03d-127">Seleziona la classe Photon View (Visualizzazione Photon) visualizzata nell'elenco a discesa.</span><span class="sxs-lookup"><span data-stu-id="aa03d-127">Select the Photon View class that appears in the drop-down list.</span></span>

    ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="aa03d-129">Fai clic sull'icona File relativa alla classe Generic Net Sync (Sincronizzazione rete generica).</span><span class="sxs-lookup"><span data-stu-id="aa03d-129">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="aa03d-130">Seleziona e trascina tale icona nel campo Observed Components (Componenti osservati) di Photon View (Visualizzazione Photon).</span><span class="sxs-lookup"><span data-stu-id="aa03d-130">Drag and drop it in the Photon View's Observed Components field.</span></span>

    ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png)

7. <span data-ttu-id="aa03d-132">Successivamente, creiamo sfere che rappresentano ogni persona che partecipa a un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="aa03d-132">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="aa03d-133">Fai clic con il pulsante destro del mouse sull'oggetto PhotonUser creato, scorri verso il basso fino a 3D Object (Oggetto 3D) e scegli Sphere (Sfera).</span><span class="sxs-lookup"><span data-stu-id="aa03d-133">Right-click the PhotonUser object you just created, scroll-down to "3D Object and click Sphere.</span></span> <span data-ttu-id="aa03d-134">Verrà creato un oggetto gioco a forma di sfera come elemento figlio dell'oggetto PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="aa03d-134">This will create a sphere game object as a child of the PhotonUser object.</span></span>

    ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="aa03d-136">Ridimensiona la sfera a x = 0,06, y = 0,06 e z = 0,06.</span><span class="sxs-lookup"><span data-stu-id="aa03d-136">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

    ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="aa03d-138">Trascina l'oggetto gioco PhotonUser nella cartella Prefabs (Prefab) del riquadro Project (Progetto) e quindi eliminalo dalla scena.</span><span class="sxs-lookup"><span data-stu-id="aa03d-138">Drag the PhotonUser game object into the Prefabs folder in the Project panel and then delete it from the scene.</span></span> <span data-ttu-id="aa03d-139">Hai ora creato un prefab che può essere usato durante la generazione o la creazione di istanze di nuovi giocatori nell'ambito di un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="aa03d-139">You have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

    ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

    >[!NOTE]
    ><span data-ttu-id="aa03d-141">Verifica che l'oggetto gioco sia stato copiato nella cartella Prefabs (Prefab) prima di eliminarlo dalla gerarchia.</span><span class="sxs-lookup"><span data-stu-id="aa03d-141">Ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="aa03d-142">Crea un nuovo oggetto nella gerarchia seguendo le istruzioni fornite nel passaggio 3 e assegna a tale oggetto il nome SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="aa03d-142">Create a new object in the hierarchy by following the instructions in Step 3 and name it SharedPlayground.</span></span> <span data-ttu-id="aa03d-143">Fai quindi clic su Add Component (Aggiungi componente) e cerca Generic Network Manager (Gestione rete generica).</span><span class="sxs-lookup"><span data-stu-id="aa03d-143">Then, click Add Component and search for generic network manager.</span></span>  <span data-ttu-id="aa03d-144">Fai clic di nuovo per aggiungere il componente Generic Network Manager (Gestione rete generica).</span><span class="sxs-lookup"><span data-stu-id="aa03d-144">Click it again to add the Generic Network Manager component.</span></span> <span data-ttu-id="aa03d-145">Modifica la posizione dell'oggetto in x = 0, y = 0 e z = 0.</span><span class="sxs-lookup"><span data-stu-id="aa03d-145">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)

## <a name="congratulations"></a><span data-ttu-id="aa03d-147">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="aa03d-147">Congratulations</span></span>

<span data-ttu-id="aa03d-148">Dopo aver completato tutti i passaggi precedenti e il processo di compilazione, premi il pulsante Play (Esegui) e connetti il dispositivo HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="aa03d-148">Once all the steps above are complete and the build process is also complete, press the Play button and connect your HoloLens 2.</span></span> <span data-ttu-id="aa03d-149">Vedrai una sfera che si muove quando muovi la testa.</span><span class="sxs-lookup"><span data-stu-id="aa03d-149">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="aa03d-150">Tale oggetto verrà visualizzato per qualsiasi utente che partecipa al progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="aa03d-150">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="aa03d-151">[Lezione successiva: 4. Condivisione dei movimenti di oggetti con più utenti](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="aa03d-151">[Next Lesson: 4. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch4.md)</span></span>

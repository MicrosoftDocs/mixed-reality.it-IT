---
title: Modulo di Base Learning MR - risolutori e posizionamento del contenuto dinamico
description: Completare questo corso di informazioni su come implementare il riconoscimento di volti di Azure all'interno di un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, hololens, esercitazione di unity,
ms.openlocfilehash: b212812beeff54bb1f92ccbcc923ab9c301945b7
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929553"
---
# <a name="mr-learning-base-module---dynamic-content-placement-and-solvers"></a><span data-ttu-id="6460b-104">Modulo di Base Learning MR - risolutori e posizionamento del contenuto dinamico</span><span class="sxs-lookup"><span data-stu-id="6460b-104">MR Learning Base Module - Dynamic Content Placement and Solvers</span></span>

<span data-ttu-id="6460b-105">Ologrammi vita caratterizzati da in 2 HoloLens quando seguire l'utente in modo intuitivo e vengono inseriti nell'ambiente fisico in modo da semplificare l'interazione semplice ed elegante.</span><span class="sxs-lookup"><span data-stu-id="6460b-105">Holograms come to life in the HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="6460b-106">Nella lezione 3, verranno analizzati i modi per inserire in modo dinamico vntana usando gli strumenti disponibili posizionamento del MRTK, noti come "risolutori".</span><span class="sxs-lookup"><span data-stu-id="6460b-106">In Lesson 3, we will explore ways to dynamically place holograms using the MRTK’s available placement tools, known as "solvers."</span></span> <span data-ttu-id="6460b-107">Il modo in cui che vengono risolti gli algoritmi complessi posizionamento spaziali sono note come "risolutori".</span><span class="sxs-lookup"><span data-stu-id="6460b-107">They are known as "solvers" for the way they solve complex spatial placement algorithms.</span></span> <span data-ttu-id="6460b-108">Nel MRTK risolutori costituiscono un sistema di script e i comportamenti che utilizziamo per essere in grado di consentire agli elementi dell'interfaccia utente seguire l'utente, l'utente o altri oggetti del gioco nella scena.</span><span class="sxs-lookup"><span data-stu-id="6460b-108">In the MRTK, solvers are a system of scripts and behaviors that we use to be able to allow UI elements to follow you, the user or other game objects in the scene.</span></span> <span data-ttu-id="6460b-109">Possono anche essere utilizzati per determinate posizioni allineare in modo rapido, rendendo più intuitivo dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="6460b-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span> 

## <a name="objectives"></a><span data-ttu-id="6460b-110">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="6460b-110">Objectives</span></span>

* <span data-ttu-id="6460b-111">Introdurre Risolutori di MRTK</span><span class="sxs-lookup"><span data-stu-id="6460b-111">Introduce the MRTK's solvers</span></span>
* <span data-ttu-id="6460b-112">Risolutori di utilizzo per avere una raccolta di pulsanti di seguono l'utente</span><span class="sxs-lookup"><span data-stu-id="6460b-112">Use solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="6460b-113">Risolutori di utilizzo per avere un oggetto gioco seguono mani registrati dell'utente</span><span class="sxs-lookup"><span data-stu-id="6460b-113">Use solvers to have a game object follow the user's tracked hands</span></span>

## <a name="instructions"></a><span data-ttu-id="6460b-114">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="6460b-114">Instructions</span></span>

### <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="6460b-115">Posizione dei risolutori nel MRTK</span><span class="sxs-lookup"><span data-stu-id="6460b-115">Location of solvers in the MRTK</span></span>
 <span data-ttu-id="6460b-116">Per trovare i risolutori disponibili nel progetto, cercare nella cartella MRTK SDK (MixedRealityToolkit.SDK cartella), quindi nella cartella utilities si verrà visualizzata la cartella risolutori, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="6460b-116">To find the available solvers in your project, look in the MRTK SDK folder (MixedRealityToolkit.SDK folder), then under the utilities folder you will see the solvers folder, as shown in the image below.</span></span>

![Risolutori](images/lesson3_chapter1_step1im.PNG)

><span data-ttu-id="6460b-118">Nota: In questa lezione verranno esaminate solo sull'implementazione del Risolutore "Orbital" e il Risolutore "RadialView".</span><span class="sxs-lookup"><span data-stu-id="6460b-118">Note: In this lesson we will only go over implementation of the "Orbital" solver and the "RadialView" solver.</span></span> <span data-ttu-id="6460b-119">Per altre informazioni sull'intervallo completo di risolutori disponibile nel MRTK, visitare: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span><span class="sxs-lookup"><span data-stu-id="6460b-119">To learn more about the full range of solvers available in the MRTK, please visit: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span></span>

### <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="6460b-120">Usare un Risolutore per seguire l'utente</span><span class="sxs-lookup"><span data-stu-id="6460b-120">Use a Solver to Follow the User</span></span>
<span data-ttu-id="6460b-121">L'obiettivo di questo capitolo è migliorare l'insieme di pulsanti creata in precedenza in modo che segua direzione sguardo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="6460b-121">The goal of this chapter is to enhance the button collection we previously created such that it follows the user’s gaze direction.</span></span> <span data-ttu-id="6460b-122">Nella versione precedente del MRTK e HoloToolkit, questa è stata definita come una funzionalità di "taglong".</span><span class="sxs-lookup"><span data-stu-id="6460b-122">In previous version of the MRTK and HoloToolkit, this was referred to as a "taglong" functionality.</span></span>

1. <span data-ttu-id="6460b-123">Selezionare l'oggetto padre di insieme di pulsanti nella lezione precedente.</span><span class="sxs-lookup"><span data-stu-id="6460b-123">Select the Button Collection parent object from the previous lesson.</span></span>

![Lezione 3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. <span data-ttu-id="6460b-125">Nel Pannello di controllo, fare clic sul pulsante "Aggiungi componente" e cercare "orbitali".</span><span class="sxs-lookup"><span data-stu-id="6460b-125">In the inspector panel, click the "add component" button and search for "orbital."</span></span> <span data-ttu-id="6460b-126">Il componente orbital dovrebbe essere visualizzato.</span><span class="sxs-lookup"><span data-stu-id="6460b-126">The orbital component should appear.</span></span> <span data-ttu-id="6460b-127">Selezionare il componente orbital all'oggetto gioco insieme di pulsanti.</span><span class="sxs-lookup"><span data-stu-id="6460b-127">Select it to add the orbital component to the Button Collection game object.</span></span>

![Lezione 3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

><span data-ttu-id="6460b-129">Nota: Quando si aggiunge il componente si noterà che il sistema consente di aggiungere lo script orbital e lo script di gestore del Risolutore nella scheda inspector, che è un componente obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="6460b-129">Note: When you add the component you will notice that the system adds the orbital script and the solver handler script in the inspector tab, which is a required component.</span></span> 

3. <span data-ttu-id="6460b-130">Per configurare l'insieme di pulsanti per seguire l'utente, è necessario implementare le modifiche seguenti (vedere anche l'immagine seguente):</span><span class="sxs-lookup"><span data-stu-id="6460b-130">In order to configure the button collection to follow the user, we need to implement the following adjustments (please also refer to the image below):</span></span>
- <span data-ttu-id="6460b-131">Nello script Orbital, impostare l'elenco di riepilogo a discesa "tipo di orientamento" a "Solo rotazione".</span><span class="sxs-lookup"><span data-stu-id="6460b-131">In the Orbital script, set the "orientation type" drop-down list to "Yaw Only."</span></span> <span data-ttu-id="6460b-132">In questo modo, in modo che solo un asse dell'oggetto ruota come indicato di seguito l'utente.</span><span class="sxs-lookup"><span data-stu-id="6460b-132">This makes it so that only one axis of the object rotates as it follows the user.</span></span>
- <span data-ttu-id="6460b-133">Impostare l'offset locale su 0 in tutti gli assi.</span><span class="sxs-lookup"><span data-stu-id="6460b-133">Set the local offset to 0 on all axes.</span></span> <span data-ttu-id="6460b-134">Impostare l'Offset del mondo su x = 0, y = -0.1 e z = 0,6.</span><span class="sxs-lookup"><span data-stu-id="6460b-134">Set the World Offset to x = 0, y = -0.1 and z = 0.6.</span></span> <span data-ttu-id="6460b-135">Questo blocca lo spostamento dell'oggetto in modo che quando l'utente modifica l'altezza, l'oggetto rimarrà abbia un'altezza fissa dell'ambiente fisico, consentendo comunque seguire l'utente quando l'utente sposta sull'ambiente.</span><span class="sxs-lookup"><span data-stu-id="6460b-135">This locks movement of the object such that when the user changes height, the object will remain at a fixed height in the physical environment, while still allowing it to follow the user as the user moves about the environment.</span></span> <span data-ttu-id="6460b-136">Questi valori possono essere modificati per ottenere un intervallo wade dei comportamenti.</span><span class="sxs-lookup"><span data-stu-id="6460b-136">These values may be adjusted to achieve a wade range of behaviors.</span></span>
- <span data-ttu-id="6460b-137">Per un comportamento seguire in base al quale i pulsanti seguono solo la visualizzazione dell'utente dopo che l'utente diventa sufficientemente testa la propria, è possibile selezionare la casella di controllo "Usa angolo esecuzione di un'istruzione per l'offset world" (Nota: Questo titolo potrebbe essere troncato in alcune schermate, come nell'immagine seguente.) Ad esempio, affinché l'oggetto seguire l'utente solo ogni 90 gradi, impostare il numero di passaggi uguale a 4 (contrassegnati da una freccia verde nell'esempio a sinistra).</span><span class="sxs-lookup"><span data-stu-id="6460b-137">For a follow behavior whereby the buttons only follow the user’s view after the user turns his or her head sufficiently far, you could select the "Use Angle Stepping for world offset" checkbox (Note: This title may be truncated on some screens, as it is in the image below.) For example, to have the object follow the user only every 90 degrees, set the number of steps equal to 4 (marked by a green arrow in the example to the left).</span></span> 

![Lezione 3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="6460b-139">Consentire agli oggetti di seguire le mani rilevate</span><span class="sxs-lookup"><span data-stu-id="6460b-139">Enabling Objects to Follow Tracked Hands</span></span>

<span data-ttu-id="6460b-140">In questa sezione si configurerà l'oggetto gioco cubo creato in precedenza per seguire le mani rilevate dell'utente con il Risolutore RadialView.</span><span class="sxs-lookup"><span data-stu-id="6460b-140">In this section, we will configure the cube game object previously created to follow the user’s tracked hands using the RadialView solver.</span></span>

1. <span data-ttu-id="6460b-141">Selezionare l'oggetto cubo nella gerarchia di BaseScene.</span><span class="sxs-lookup"><span data-stu-id="6460b-141">Select the cube object in the BaseScene hierarchy.</span></span> <span data-ttu-id="6460b-142">Fare clic su "Aggiungi componente" nel Pannello di controllo.</span><span class="sxs-lookup"><span data-stu-id="6460b-142">Click "add component" in the inspector panel.</span></span> 

![Lezione 3 Chapter3 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. <span data-ttu-id="6460b-144">Digitare "RadialView" nella casella di ricerca e selezionare il componente RadialView per aggiungerlo al cubo.</span><span class="sxs-lookup"><span data-stu-id="6460b-144">Type in "RadialView" in the search box and select the RadialView component to add it to the cube.</span></span> <span data-ttu-id="6460b-145">Il componente gestore Risolutore anche verrà aggiunto automaticamente al cubo.</span><span class="sxs-lookup"><span data-stu-id="6460b-145">The solver handler component will also be automatically added to the cube.</span></span>

3. <span data-ttu-id="6460b-146">Modificare la visualizzazione radiale per non seguire la testa ma si attengono a sinistra.</span><span class="sxs-lookup"><span data-stu-id="6460b-146">Change the radial view to not follow the head but follow the left hand.</span></span> <span data-ttu-id="6460b-147">Selezionare il menu a discesa accanto all'opzione "rilevati oggetti per fare riferimento a".</span><span class="sxs-lookup"><span data-stu-id="6460b-147">Select the dropdown menu next to the "tracked object to reference" option.</span></span> <span data-ttu-id="6460b-148">Quindi selezionare "passare giunto a sinistra" dal menu di scelta.</span><span class="sxs-lookup"><span data-stu-id="6460b-148">Then select "hand joint left" from the menu.</span></span>

![Lezione 3 Chapter3 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. <span data-ttu-id="6460b-150">Dopo aver selezionato la giunzione manualmente, è possibile scegliere quale parte della lancetta desiderato del cubo da seguire.</span><span class="sxs-lookup"><span data-stu-id="6460b-150">Once you select the hand joint, you can choose which part of the hand you want the cube to follow.</span></span> <span data-ttu-id="6460b-151">In questo esempio si userà il polso.</span><span class="sxs-lookup"><span data-stu-id="6460b-151">For this example, we are going to use the wrist.</span></span> <span data-ttu-id="6460b-152">Accanto all'opzione "joint mano rilevate" selezionare il menu a discesa e selezionare polso.</span><span class="sxs-lookup"><span data-stu-id="6460b-152">Next to the option "tracked hand joint" select the dropdown menu and select wrist.</span></span> 

![Lezione 3 Chapter3 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. <span data-ttu-id="6460b-154">Impostare le distanze massime e minime su 0 in modo che il cubo non avrà alcun distanza tra i dati e del polso dell'utente.</span><span class="sxs-lookup"><span data-stu-id="6460b-154">Set the maximum and minimum distances to 0 so that the cube will not have any distance between it and the user’s wrist.</span></span> <span data-ttu-id="6460b-155">Una volta impostato, il cubo verrà essere perfettamente allineato con il polso.</span><span class="sxs-lookup"><span data-stu-id="6460b-155">Once set, the cube will be perfectly aligned with the wrist.</span></span> <span data-ttu-id="6460b-156">È anche possibile modificare il campo "Riferimento direzione" per modificare il comportamento del modo in cui il cubo è orientata ai servizi (ad esempio, se si vuole consentire l'oggetto ruota con polso dell'utente, impostare la direzione di riferimento a "Orienta con oggetto rilevate")</span><span class="sxs-lookup"><span data-stu-id="6460b-156">You may also adjust the "Reference Direction" field to adjust the behavior of how the cube is oriented (e.g., if you would like to allow the object to rotate with the user's wrist, set the reference direction to "Orient with Tracked Object")</span></span>

![Lezione 3 Chapter3 Step5im](images/Lesson3_chapter3_step5im.PNG)

### <a name="congratulations"></a><span data-ttu-id="6460b-158">È stata completata</span><span class="sxs-lookup"><span data-stu-id="6460b-158">Congratulations</span></span>
<span data-ttu-id="6460b-159">La procedura è stata completata.</span><span class="sxs-lookup"><span data-stu-id="6460b-159">Congratulations!</span></span> <span data-ttu-id="6460b-160">In questa lezione è stato descritto come utilizzare Risolutori di MRTK per avere un'interfaccia utente in modo intuitivo seguire l'utente.</span><span class="sxs-lookup"><span data-stu-id="6460b-160">In this lesson, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="6460b-161">Inoltre appreso come collegare un Risolutore a un oggetto gioco (vale a dire, cubo) seguire mani registrati dell'utente.</span><span class="sxs-lookup"><span data-stu-id="6460b-161">You also learned how to attach a solver to a game object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="6460b-162">Per altre informazioni su questi e altri risolutori inclusi con il MRTK, è possibile visitare il [pagina della documentazione risolutori MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).</span><span class="sxs-lookup"><span data-stu-id="6460b-162">To learn more about these and other solvers included with the MRTK, feel free to visit the [MRTK solvers documentation page](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).</span></span>

[<span data-ttu-id="6460b-163">Lezione successiva: Interazione dell'oggetto 3D</span><span class="sxs-lookup"><span data-stu-id="6460b-163">Next Lesson: 3D Object Interaction</span></span>](mrlearning-base-ch4.md)

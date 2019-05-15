---
title: Visualizzazioni delle app
description: I due tipi di visualizzazioni nelle app di realtà mista di Windows sono coinvolgenti visualizzazioni e visualizzazioni 2D.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: visualizzazione coinvolgente e concreto di app visualizzazione 2D, slate,
ms.openlocfilehash: 2cf65941616ac6906d40e4b4616311317ac705d3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604730"
---
# <a name="app-views"></a><span data-ttu-id="22a4f-104">Visualizzazioni delle app</span><span class="sxs-lookup"><span data-stu-id="22a4f-104">App views</span></span>

<span data-ttu-id="22a4f-105">Le app di Windows possono contenere due tipi di visualizzazioni, **visualizzazioni coinvolgenti** e **visualizzazioni 2D**.</span><span class="sxs-lookup"><span data-stu-id="22a4f-105">Windows apps can contain two kinds of views, **immersive views** and **2D views**.</span></span> <span data-ttu-id="22a4f-106">Le app possono passare tra le diverse visualizzazioni coinvolgenti e visualizzazioni 2D, che mostra le visualizzazioni 2D in un monitor come finestra o in un auricolare come uno slate.</span><span class="sxs-lookup"><span data-stu-id="22a4f-106">Apps can switch between their various immersive views and 2D views, showing their 2D views either on a monitor as a window or in a headset as a slate.</span></span> <span data-ttu-id="22a4f-107">Le app che hanno almeno una visualizzazione immersiva categorizzate come **le App per realtà mista**.</span><span class="sxs-lookup"><span data-stu-id="22a4f-107">Apps that have at least one immersive view are categorized as **mixed reality apps**.</span></span> <span data-ttu-id="22a4f-108">Sono App che non hanno mai una vista coinvolgente **2D app**.</span><span class="sxs-lookup"><span data-stu-id="22a4f-108">Apps that never have a immersive view are **2D apps**.</span></span>

## <a name="immersive-views"></a><span data-ttu-id="22a4f-109">Visualizzazioni coinvolgenti</span><span class="sxs-lookup"><span data-stu-id="22a4f-109">Immersive views</span></span>

<span data-ttu-id="22a4f-110">Una vista immersiva consente all'app la possibilità di creare vntana in tutto il mondo si o immersion sull'utente in un ambiente virtuale.</span><span class="sxs-lookup"><span data-stu-id="22a4f-110">An immersive view gives your app the ability to create holograms in the world around you or immerse the user in a virtual environment.</span></span> <span data-ttu-id="22a4f-111">Quando si disegna un'app nella visualizzazione coinvolgente, non disegna nessuna altra app nello stesso momento&mdash;vntana da più App è composti non insieme.</span><span class="sxs-lookup"><span data-stu-id="22a4f-111">When an app is drawing in the immersive view, no other app is drawing at the same time&mdash;holograms from multiple apps are not composited together.</span></span> <span data-ttu-id="22a4f-112">Regolando continuamente la prospettiva da cui il [app esegue il rendering](rendering.md) la scena in modo che corrispondano spostamenti head dell'utente, l'app può eseguire il rendering [bloccato world](coordinate-systems.md) vntana che rimangono in un punto fisso in realtà World oppure può eseguire il rendering di un mondo virtuale che contiene la posizione, mentre un utente si sposta all'interno di esso.</span><span class="sxs-lookup"><span data-stu-id="22a4f-112">By continually adjusting the perspective from which your [app renders](rendering.md) its scene to match the user's head movements, your app can render [world-locked](coordinate-systems.md) holograms that remain at a fixed point in the real world, or it can render a virtual world that holds its position as a user moves within it.</span></span>

<span data-ttu-id="22a4f-113">![Quando in una visualizzazione coinvolgente, vntana può essere inserito in tutto il mondo si.](images/designoverview.jpg)</span><span class="sxs-lookup"><span data-stu-id="22a4f-113">![When in an immersive view, holograms can be placed in the world around you.](images/designoverview.jpg)</span></span><br>
<span data-ttu-id="22a4f-114">*Quando in una visualizzazione coinvolgente, vntana può essere inserito in tutto il mondo si*</span><span class="sxs-lookup"><span data-stu-id="22a4f-114">*When in an immersive view, holograms can be placed in the world around you*</span></span>

<span data-ttu-id="22a4f-115">Sul [HoloLens](hololens-hardware-details.md), l'app esegue il rendering relativi vntana sopra automobilista reale dell'utente.</span><span class="sxs-lookup"><span data-stu-id="22a4f-115">On [HoloLens](hololens-hardware-details.md), your app renders its holograms on top of the user's real-world surroundings.</span></span> <span data-ttu-id="22a4f-116">In un [visore VR immersivi di realtà mista di Windows](immersive-headset-hardware-details.md), l'utente non è possibile visualizzare il modo reale e in modo che l'app deve eseguire il rendering di tutto ciò che verrà visualizzato all'utente.</span><span class="sxs-lookup"><span data-stu-id="22a4f-116">On a [Windows Mixed Reality immersive headset](immersive-headset-hardware-details.md), the user cannot see the real world, and so your app must render everything the user will see.</span></span>

<span data-ttu-id="22a4f-117">Il [realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md) (incluso nel menu Start e vntana è stato inserito tutto l'ambiente) non esegue il rendering in un coinvolgenti visualizzare entrambi.</span><span class="sxs-lookup"><span data-stu-id="22a4f-117">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) (including the Start menu and holograms you've placed around the environment) does not render while in an immersive view either.</span></span> <span data-ttu-id="22a4f-118">Le notifiche di sistema che si verificano mentre è visualizzata una vista immersiva verranno inoltrate acustico da parte di Cortana su HoloLens, e l'utente può rispondere con input vocale.</span><span class="sxs-lookup"><span data-stu-id="22a4f-118">On HoloLens, any system notifications that occur while an immersive view is showing will be relayed audibly by Cortana, and the user can respond with voice input.</span></span>

<span data-ttu-id="22a4f-119">Mentre in una visualizzazione coinvolgente, l'app è anche responsabile della gestione di tutti gli input.</span><span class="sxs-lookup"><span data-stu-id="22a4f-119">While in an immersive view, your app is also responsible for handling all input.</span></span> <span data-ttu-id="22a4f-120">Input nella realtà mista di Windows è costituito da [estasiati](gaze.md), [movimento](gestures.md) (solo HoloLens), [vocali](voice-input.md) e [movimento controller](motion-controllers.md) (coinvolgenti auricolari solo).</span><span class="sxs-lookup"><span data-stu-id="22a4f-120">Input in Windows Mixed Reality is made up of [gaze](gaze.md), [gesture](gestures.md) (HoloLens only), [voice](voice-input.md) and [motion controllers](motion-controllers.md) (immersive headsets only).</span></span>

## <a name="2d-views"></a><span data-ttu-id="22a4f-121">Visualizzazioni 2D</span><span class="sxs-lookup"><span data-stu-id="22a4f-121">2D views</span></span>

<span data-ttu-id="22a4f-122">![Più visualizzazioni 2D disposto intorno a casa la realtà mista di Windows](images/teleportation-640px.png)</span><span class="sxs-lookup"><span data-stu-id="22a4f-122">![Multiple 2D views laid out around the Windows Mixed Reality home](images/teleportation-640px.png)</span></span><br>
<span data-ttu-id="22a4f-123">*Più App con una visualizzazione 2D per racchiudere la realtà mista di Windows home*</span><span class="sxs-lookup"><span data-stu-id="22a4f-123">*Multiple apps with a 2D view placed around the Windows Mixed Reality home*</span></span>

<span data-ttu-id="22a4f-124">Viene visualizzata un'app con una visualizzazione 2D il [realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md) (operazione talvolta denominata "shell") come uno slate virtuale, viene eseguito il rendering con l'utilità di avvio di app e altri vntana l'utente ha effettuato nel proprio mondo.</span><span class="sxs-lookup"><span data-stu-id="22a4f-124">An app with a 2D view appears in the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) (sometimes called the "shell") as a virtual slate, rendered alongside the app launchers and other holograms the user has placed in their world.</span></span> <span data-ttu-id="22a4f-125">L'utente può regolare questa lavagna per spostare e ridimensionare, anche se rimane una risoluzione fissa indipendentemente dalle dimensioni.</span><span class="sxs-lookup"><span data-stu-id="22a4f-125">The user can adjust this slate to move and scale it, though it remains at a fixed resolution regardless of its size.</span></span> <span data-ttu-id="22a4f-126">Se prima visualizzazione dell'app è una visualizzazione 2D, il contenuto 2D riempirà lo slate stesso utilizzato per avviare l'app.</span><span class="sxs-lookup"><span data-stu-id="22a4f-126">If your app's first view is a 2D view, your 2D content will fill the same slate used to launch the app.</span></span>

<span data-ttu-id="22a4f-127">In un auricolare desktop, è possibile eseguire qualsiasi App Universal Windows Platform (UWP) eseguite sullo schermo desktop oggi stesso.</span><span class="sxs-lookup"><span data-stu-id="22a4f-127">In a desktop headset, you can run any Universal Windows Platform (UWP) apps that run on your desktop monitor today.</span></span> <span data-ttu-id="22a4f-128">Queste App sono già rendering delle visualizzazioni 2D oggi stesso e il relativo contenuto verrà visualizzati automaticamente in un Tablet nel mondo dell'utente all'avvio.</span><span class="sxs-lookup"><span data-stu-id="22a4f-128">These apps are already rendering 2D views today, and their content will automatically appear on a slate in the user's world when launched.</span></span> <span data-ttu-id="22a4f-129">Le app UWP 2D possono avere come destinazione il **Universal** famiglia di dispositivi per l'esecuzione in entrambe le cuffie desktop e in HoloLens come Slate.</span><span class="sxs-lookup"><span data-stu-id="22a4f-129">2D UWP apps can target the **Windows.Universal** device family to run on both desktop headsets and on HoloLens as slates.</span></span>

<span data-ttu-id="22a4f-130">Uno degli utilizzi principali del visualizzazioni 2D sono illustrare un form di immissione di testo che può rendere l'utilizzo di tastiera del sistema.</span><span class="sxs-lookup"><span data-stu-id="22a4f-130">One key use of 2D views is to show a text entry form that can make use of the system keyboard.</span></span> <span data-ttu-id="22a4f-131">Poiché la shell non è possibile eseguire il rendering nella parte superiore di una vista coinvolgente, l'app deve passare a una visualizzazione 2D per mostrare i tasti di sistema.</span><span class="sxs-lookup"><span data-stu-id="22a4f-131">Because the shell cannot render on top of an immersive view, the app must switch to a 2D view to show the system keyboard.</span></span> <span data-ttu-id="22a4f-132">Le app che desidera accettare input di testo è possono passare a una visualizzazione 2D con una casella di testo.</span><span class="sxs-lookup"><span data-stu-id="22a4f-132">Apps that want to accept text input can switch to a 2D view with a text box.</span></span> <span data-ttu-id="22a4f-133">Mentre tale casella di testo ha lo stato attivo, il sistema visualizza la tastiera del sistema, consentendo all'utente di immettere testo.</span><span class="sxs-lookup"><span data-stu-id="22a4f-133">While that text box has focus, the system will show the system keyboard, allowing the user to enter text.</span></span>

<span data-ttu-id="22a4f-134">Si noti che in un PC desktop, un'app può avere visualizzazioni 2D in entrambi i monitor da tavolo e in un auricolare collegati.</span><span class="sxs-lookup"><span data-stu-id="22a4f-134">Note that on a desktop PC, an app can have 2D views on both the desktop monitor and in an attached headset.</span></span> <span data-ttu-id="22a4f-135">Ad esempio, è possibile esplorare Edge sullo schermo desktop usando la relativa visualizzazione 2D principale per trovare un video a 360 gradi.</span><span class="sxs-lookup"><span data-stu-id="22a4f-135">For example, you can browse Edge on your desktop monitor using its main 2D view to find a 360-degree video.</span></span> <span data-ttu-id="22a4f-136">Quando si riproduce video specifico, Edge avvierà una visualizzazione immersiva secondaria all'interno delle cuffie, possono visualizzare il contenuto video coinvolgente.</span><span class="sxs-lookup"><span data-stu-id="22a4f-136">When you play that video, Edge will launch a secondary immersive view inside the headset to display the immersive video content.</span></span>

## <a name="see-also"></a><span data-ttu-id="22a4f-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="22a4f-137">See also</span></span>

* [<span data-ttu-id="22a4f-138">Modello di App</span><span class="sxs-lookup"><span data-stu-id="22a4f-138">App model</span></span>](app-model.md)
* [<span data-ttu-id="22a4f-139">L'aggiornamento di App UWP 2D per realtà mista</span><span class="sxs-lookup"><span data-stu-id="22a4f-139">Updating 2D UWP apps for mixed reality</span></span>](building-2d-apps.md)
* [<span data-ttu-id="22a4f-140">Ottenere un HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="22a4f-140">Getting a HolographicSpace</span></span>](getting-a-holographicspace.md)
* [<span data-ttu-id="22a4f-141">Esplorazione di realtà mista di Windows home</span><span class="sxs-lookup"><span data-stu-id="22a4f-141">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="22a4f-142">Tipi di App di realtà mista</span><span class="sxs-lookup"><span data-stu-id="22a4f-142">Types of mixed reality apps</span></span>](types-of-mixed-reality-apps.md)
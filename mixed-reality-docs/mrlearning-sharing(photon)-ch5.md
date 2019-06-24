---
title: MR Learning condivisione del modulo per HoloLens 2
description: Completare questo corso di informazioni su come implementare esperienze condivise con più utenti all'interno di un'applicazione 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 9f4a0c0cc37ab097a60c44891d56fa65f6032418
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327190"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="bfbed-104">Gli ancoraggi spaziali Azure ed esperienze condivise</span><span class="sxs-lookup"><span data-stu-id="bfbed-104">Azure Spatial Anchors and Shared Experiences</span></span>

<span data-ttu-id="bfbed-105">In questa lezione, si verrà descrive come integrare Azure spaziali Anchor (ASA) nella nostra esperienza condiviso.</span><span class="sxs-lookup"><span data-stu-id="bfbed-105">In this lesson, we will learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="bfbed-106">ASA consente a più dispositivi con risorse condivise per avere una conoscenza comune se si verifica nel proprio ambiente fisico per ancorare virtuale in modo che tutti i partecipanti di visualizzare gli oggetti nella stessa posizione fisica.</span><span class="sxs-lookup"><span data-stu-id="bfbed-106">ASA allows multiple co-located devices to have a common understanding if their physical environment in order to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="bfbed-107">Prima di procedere con questa lezione, è necessario completare il modulo di apprendimento ASA, che si occuperà ASA nozioni di base, account di Azure e la creazione di risorse e altri blocchi di edifici fondamentali che sono necessari affinché possiamo integrare ASA nella nostra esperienza condiviso.</span><span class="sxs-lookup"><span data-stu-id="bfbed-107">Before proceeding with this lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="bfbed-108">Obiettivi:</span><span class="sxs-lookup"><span data-stu-id="bfbed-108">Objectives:</span></span>

- <span data-ttu-id="bfbed-109">Integrare un'esperienza condivisa per l'allineamento di più dispositivi ASA</span><span class="sxs-lookup"><span data-stu-id="bfbed-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
- <span data-ttu-id="bfbed-110">Scopri le nozioni di base del funzionamento nel contesto di un'esperienza condiviso locale ASA</span><span class="sxs-lookup"><span data-stu-id="bfbed-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="bfbed-111">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="bfbed-111">Instructions</span></span>

1. <span data-ttu-id="bfbed-112">Salvare il progetto nella lezione precedente (CTRL + S) e denominarlo "HLSharedProjectMainPart5.unity" in modo che risulti più facile individuare quando è necessario anche in questo caso.</span><span class="sxs-lookup"><span data-stu-id="bfbed-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="bfbed-113">Selezionare il prefab TableAnchor sotto l'oggetto padre "MixedRealityPlayspace" ed eliminarla.</span><span class="sxs-lookup"><span data-stu-id="bfbed-113">Select the TableAnchor prefab underneath  the "MixedRealityPlayspace" parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3. <span data-ttu-id="bfbed-115">Proprio come alcune delle lezioni precedenti, importare un nuovo pacchetto personalizzato che è possibile ottenere [qui.](placeholderlink)</span><span class="sxs-lookup"><span data-stu-id="bfbed-115">Just like some of the previous lessons, import a new custom package that you can get [here.](placeholderlink)</span></span>

![Module3Chapter5step3im](images/module3chapter5step3im.PNG)

4. <span data-ttu-id="bfbed-117">Una volta che viene importato, recuperare il punto di ancoraggio tabella appena aggiornata (dal pacchetto unity importato nel passaggio precedente) dalla cartella "prefabs" nel Pannello di progetto e rilasciarlo nell'oggetto padre "MixedRealityPlayspace."</span><span class="sxs-lookup"><span data-stu-id="bfbed-117">Once it's imported, grab the newly updated table anchor (from the unity package imported in the previous step) from the "prefabs" folder in the project panel and drop it into the parent object "MixedRealityPlayspace."</span></span>

![Module3hapter5step4im](images/module3chapter5step4im.PNG)

5. <span data-ttu-id="bfbed-119">Espandere l'oggetto padre "MixedRealityPlayspace", quindi l'oggetto "TableAnchor" e anche l'oggetto "pulsanti".</span><span class="sxs-lookup"><span data-stu-id="bfbed-119">Expand the "MixedRealityPlayspace" parent object, then the "TableAnchor" object, and expand the "buttons" object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

6. <span data-ttu-id="bfbed-121">A questo punto della gerarchia, selezionare "ShareAzureAnchorButton" e spostare l'attenzione dell'utente al pannello di controllo.</span><span class="sxs-lookup"><span data-stu-id="bfbed-121">Now in the hierarchy, select the "ShareAzureAnchorButton" and move your attention to the inspector panel.</span></span> <span data-ttu-id="bfbed-122">Scorrere verso il basso nel menu a discesa illustrato nell'immagine seguente e selezionare "AnchorModuleScript" e fare clic su "ShareAnchorNetework()."</span><span class="sxs-lookup"><span data-stu-id="bfbed-122">Scroll down to the dropdown menu shown in the image below, and select "AnchorModuleScript" and click on "ShareAnchorNetework()."</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

7. <span data-ttu-id="bfbed-124">Analogamente al passaggio 6, selezionare "GetAzureAnchorButton" e spostare l'attenzione dell'utente al pannello di controllo.</span><span class="sxs-lookup"><span data-stu-id="bfbed-124">Much like step 6, select the "GetAzureAnchorButton" and move your attention back to the inspector panel.</span></span> <span data-ttu-id="bfbed-125">Scorrere verso il basso nel menu a discesa illustrato nell'immagine seguente e selezionare "AnchorModuleScript" e fare clic su "GetSharedAnchorNetwork()."</span><span class="sxs-lookup"><span data-stu-id="bfbed-125">Scroll down to the dropdown menu shown in the image below, and select "AnchorModuleScript" and click on "GetSharedAnchorNetwork()."</span></span> <span data-ttu-id="bfbed-126">Quindi salvare.</span><span class="sxs-lookup"><span data-stu-id="bfbed-126">Then save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a><span data-ttu-id="bfbed-128">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="bfbed-128">Congratulations</span></span>

<span data-ttu-id="bfbed-129">In questa lezione si è appreso come integrare potente nuovi spaziali Anchor Azure per allineare i dispositivi con risorse condivise in un'esperienza condiviso.</span><span class="sxs-lookup"><span data-stu-id="bfbed-129">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="bfbed-130">In questa lezione si conclude anche il modulo di condivisione.</span><span class="sxs-lookup"><span data-stu-id="bfbed-130">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="bfbed-131">Abbiamo appreso come configurare un nuovo account Photon, integrare Photon e il gioco di parole in una nuova applicazione di Unity, configurazione avatar e oggetti condivisi e infine allineamento più partecipanti tramite ASA.</span><span class="sxs-lookup"><span data-stu-id="bfbed-131">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 


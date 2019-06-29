---
title: MR Learning condivisione del modulo per HoloLens 2
description: Completare questo corso di informazioni su come implementare esperienze condivise con più utenti all'interno di un'applicazione 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 2a16d318c6d749bcbf6ed9db0d6cd2228a6ea06e
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465206"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="12ee8-104">Gli ancoraggi spaziali Azure ed esperienze condivise</span><span class="sxs-lookup"><span data-stu-id="12ee8-104">Azure Spatial Anchors and shared experiences</span></span>

<span data-ttu-id="12ee8-105">In questa lezione si descrive come integrare Azure spaziali Anchor (ASA) nella nostra esperienza condiviso.</span><span class="sxs-lookup"><span data-stu-id="12ee8-105">In this lesson, we learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="12ee8-106">ASA consente a più dispositivi con risorse condivise avere un riferimento comune se l'ambiente fisico a esperienze virtuale ancoraggio tale che tutti i partecipanti di visualizzare gli oggetti nella stessa posizione fisica.</span><span class="sxs-lookup"><span data-stu-id="12ee8-106">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="12ee8-107">Prima di procedere con questa lezione, è necessario completare il modulo di apprendimento ASA, che si occuperà ASA nozioni di base, account di Azure e la creazione di risorse e altri blocchi di edifici fondamentali che sono necessari affinché possiamo integrare ASA nella nostra esperienza condiviso.</span><span class="sxs-lookup"><span data-stu-id="12ee8-107">Before proceeding with this lesson, we'll need to complete the ASA learning module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="12ee8-108">Obiettivi:</span><span class="sxs-lookup"><span data-stu-id="12ee8-108">Objectives:</span></span>

- <span data-ttu-id="12ee8-109">Integrare un'esperienza condivisa per l'allineamento di più dispositivi ASA</span><span class="sxs-lookup"><span data-stu-id="12ee8-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
- <span data-ttu-id="12ee8-110">Scopri le nozioni di base del funzionamento nel contesto di un'esperienza condiviso locale ASA</span><span class="sxs-lookup"><span data-stu-id="12ee8-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="12ee8-111">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="12ee8-111">Instructions</span></span>

1. <span data-ttu-id="12ee8-112">Salvare il progetto nella lezione precedente (CTRL + S) e denominarlo "HLSharedProjectMainPart5.unity" in modo che risulti più facile individuare quando è necessario anche in questo caso.</span><span class="sxs-lookup"><span data-stu-id="12ee8-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="12ee8-113">Selezionare il prefab TableAnchor sotto l'oggetto padre MixedRealityPlayspace ed eliminarla.</span><span class="sxs-lookup"><span data-stu-id="12ee8-113">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)



3.  <span data-ttu-id="12ee8-115">Nella visualizzazione del progetto, selezionare gli asset -> risorse -> Prefabs e trascinare il prefab TableAnchor sopra l'oggetto SharedPlayground per renderlo un elemento figlio.</span><span class="sxs-lookup"><span data-stu-id="12ee8-115">In the Project view go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="12ee8-116">Espandere l'oggetto padre MixedRealityPlayspace, TableAnchor e anche l'oggetto di pulsanti.</span><span class="sxs-lookup"><span data-stu-id="12ee8-116">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="12ee8-118">A questo punto della gerarchia, selezionare ShareAzureAnchorButton e spostare l'attenzione dell'utente al pannello di Inaspector.</span><span class="sxs-lookup"><span data-stu-id="12ee8-118">Now in the hierarchy, select ShareAzureAnchorButton, and move your attention to the Inaspector panel.</span></span> <span data-ttu-id="12ee8-119">Scorrere verso il basso il menu di riepilogo a discesa mostrato nell'immagine seguente, AnchorModuleScript e selezionare ShareAnchorNetework().</span><span class="sxs-lookup"><span data-stu-id="12ee8-119">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript and click ShareAnchorNetework().</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="12ee8-121">Selezionare GetAzureAnchorButton (vedere Passaggio 4), e spostare l'attenzione dell'utente al pannello di controllo.</span><span class="sxs-lookup"><span data-stu-id="12ee8-121">Select GetAzureAnchorButton (see Step 4), and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="12ee8-122">Scorrere verso il basso il menu di riepilogo a discesa mostrato nell'immagine seguente e selezionare AnchorModuleScript e fare clic su GetSharedAnchorNetwork() e salvare.</span><span class="sxs-lookup"><span data-stu-id="12ee8-122">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript, and click GetSharedAnchorNetwork(), and save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a><span data-ttu-id="12ee8-124">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="12ee8-124">Congratulations</span></span>

<span data-ttu-id="12ee8-125">In questa lezione si è appreso come integrare potente nuovi spaziali Anchor Azure per allineare i dispositivi con risorse condivise in un'esperienza condiviso.</span><span class="sxs-lookup"><span data-stu-id="12ee8-125">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="12ee8-126">In questa lezione si conclude anche il modulo di condivisione.</span><span class="sxs-lookup"><span data-stu-id="12ee8-126">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="12ee8-127">Abbiamo appreso come configurare un nuovo account Photon, integrare Photon e il gioco di parole in una nuova applicazione di Unity, configurazione avatar e oggetti condivisi e infine allineamento più partecipanti tramite ASA.</span><span class="sxs-lookup"><span data-stu-id="12ee8-127">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 


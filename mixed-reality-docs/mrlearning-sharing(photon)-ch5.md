---
title: Esercitazioni sulle funzionalità multiutente-5. Integrazione di ancoraggi spaziali di Azure in un'esperienza condivisa
description: Completare questo corso per apprendere come implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 9d76d5323705c001dbafe4411a9334dd3403d0ca
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926233"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="97bfe-105">5. integrazione di ancoraggi spaziali di Azure in un'esperienza condivisa</span><span class="sxs-lookup"><span data-stu-id="97bfe-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="97bfe-106">In questa lezione si apprenderà come integrare Azure Spatial Anchors (ASA) nell'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="97bfe-106">In this lesson, you'll learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="97bfe-107">ASA consente a più dispositivi con percorso condiviso di avere un riferimento comune se l'ambiente fisico prevede l'ancoraggio di esperienze virtuali in modo che tutti i partecipanti vedano gli oggetti nella stessa posizione fisica.</span><span class="sxs-lookup"><span data-stu-id="97bfe-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="97bfe-108">Prima di procedere con questa lezione, è necessario completare il modulo ASA Learning, che riguarderà le nozioni di base di ASA, la creazione di account e risorse di Azure, nonché altri blocchi predefiniti fondamentali necessari prima di integrare ASA nell'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="97bfe-108">Before proceeding with this lesson, you'll need to complete the ASA learning module, which will cover ASA basics, Azure account and resource creation, as well as other fundamental building blocks required before integrating ASA into our shared experience.</span></span>

<span data-ttu-id="97bfe-109">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="97bfe-109">Objectives:</span></span>

- <span data-ttu-id="97bfe-110">Integrare ASA in un'esperienza condivisa per l'allineamento di più dispositivi.</span><span class="sxs-lookup"><span data-stu-id="97bfe-110">Integrate ASA into a shared experience for multi-device alignment.</span></span>
- <span data-ttu-id="97bfe-111">Informazioni sulle nozioni di base sul funzionamento di ASA nel contesto di un'esperienza condivisa locale.</span><span class="sxs-lookup"><span data-stu-id="97bfe-111">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

### <a name="instructions"></a><span data-ttu-id="97bfe-112">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="97bfe-112">Instructions</span></span>

1. <span data-ttu-id="97bfe-113">Salvare il progetto dalla lezione precedente (CTRL + S) e denominarlo "HLSharedProjectMainPart5. Unity" in modo che sia più facile da trovare quando è necessario.</span><span class="sxs-lookup"><span data-stu-id="97bfe-113">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="97bfe-114">Selezionare la prefabbricazione TableAnchor sotto l'oggetto padre MixedRealityPlayspace ed eliminarla.</span><span class="sxs-lookup"><span data-stu-id="97bfe-114">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3.  <span data-ttu-id="97bfe-116">Nella visualizzazione del progetto passare a assets-> Resources-> prefabbricates e trascinare il prefabbricato TableAnchor sull'oggetto SharedPlayground per impostarlo come figlio.</span><span class="sxs-lookup"><span data-stu-id="97bfe-116">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="97bfe-117">Espandere l'oggetto padre MixedRealityPlayspace, l'oggetto TableAnchor ed espandere anche l'oggetto Buttons.</span><span class="sxs-lookup"><span data-stu-id="97bfe-117">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="97bfe-119">A questo punto, nella gerarchia selezionare ShareAzureAnchorButton e spostare l'attenzione sul pannello Inspector.</span><span class="sxs-lookup"><span data-stu-id="97bfe-119">Now in the hierarchy, select ShareAzureAnchorButton and move your attention to the Inspector panel.</span></span> <span data-ttu-id="97bfe-120">Scorrere verso il basso fino al menu a discesa visualizzato nell'immagine seguente, selezionare AnchorModuleScript e fare clic su ShareAnchorNetwork ().</span><span class="sxs-lookup"><span data-stu-id="97bfe-120">Scroll down to the drop-down menu shown in the image below, select AnchorModuleScript and click ShareAnchorNetwork().</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="97bfe-122">Selezionare GetAzureAnchorButton (vedere il passaggio 4) e riportare l'attenzione al pannello Inspector.</span><span class="sxs-lookup"><span data-stu-id="97bfe-122">Select GetAzureAnchorButton (see Step 4) and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="97bfe-123">Scorrere verso il basso fino al menu a discesa visualizzato nell'immagine seguente, selezionare AnchorModuleScript, fare clic su GetSharedAnchorNetwork () e quindi su Save (Salva).</span><span class="sxs-lookup"><span data-stu-id="97bfe-123">Scroll down to the drop-down menu displayed in the image below, select AnchorModuleScript, click GetSharedAnchorNetwork(), and save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="97bfe-125">Per testare il modulo di condivisione, fare clic sul pulsante "Avvia sessione di Azure ASA" che avvierà la sessione di ancoraggi spaziali di Azure e quindi creare l'ancoraggio di Azure facendo clic sul pulsante "Crea ancoraggio Azure".</span><span class="sxs-lookup"><span data-stu-id="97bfe-125">To test the sharing module, click the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button.</span></span> <span data-ttu-id="97bfe-126">Attendere che l'ancoraggio di Azure venga creato.</span><span class="sxs-lookup"><span data-stu-id="97bfe-126">Wait for the azure anchor to get created.</span></span> <span data-ttu-id="97bfe-127">Dopo aver creato l'ancoraggio di Azure, fare clic sul pulsante "Condividi Azure Anchor" per condividere l'ancoraggio Azure creato dal HoloLens.</span><span class="sxs-lookup"><span data-stu-id="97bfe-127">Once the azure anchor is created, click the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

7. <span data-ttu-id="97bfe-128">Per ricevere l'ancoraggio Azure condiviso in un altro HoloLens, fare clic su "Avvia sessione di Azure ASA" per avviare e ottenere la sessione ASA corrente</span><span class="sxs-lookup"><span data-stu-id="97bfe-128">To receive the shared azure anchor in another HoloLens, click the "Start Azure ASA Session" to start and get in to the current ASA session</span></span>

8. <span data-ttu-id="97bfe-129">Fare clic sul pulsante "Get Azure Anchor" per ottenere l'ancoraggio Azure condiviso dall'altro HoloLens.</span><span class="sxs-lookup"><span data-stu-id="97bfe-129">Click the "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

   > <span data-ttu-id="97bfe-130">Nota: tutti i dettagli delle azioni corrispondenti sui singoli pulsanti verranno visualizzati nella finestra di debug.</span><span class="sxs-lookup"><span data-stu-id="97bfe-130">Note: All details of the corresponding actions on the individual buttons will be displayed in the debug window.</span></span>

## <a name="congratulations"></a><span data-ttu-id="97bfe-131">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="97bfe-131">Congratulations</span></span>

<span data-ttu-id="97bfe-132">In questa lezione si è appreso come integrare i nuovi ancoraggi spaziali avanzati di Azure per allineare i dispositivi con percorso condiviso in un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="97bfe-132">In this lesson, you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="97bfe-133">Si conclude anche il modulo sharing.</span><span class="sxs-lookup"><span data-stu-id="97bfe-133">This also concludes the Sharing Module.</span></span> <span data-ttu-id="97bfe-134">Si è appreso come configurare un nuovo account Photon, integrare Photon e PUN in una nuova applicazione Unity, configurare avatar e oggetti condivisi e infine allineare più partecipanti usando ASA.</span><span class="sxs-lookup"><span data-stu-id="97bfe-134">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configure avatars and shared objects, and finally align multiple participants using ASA.</span></span> 


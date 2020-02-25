---
title: Esercitazioni sulle funzionalità multiutente-5. Integrazione di ancoraggi spaziali di Azure in un'esperienza condivisa
description: Completare questo corso per apprendere come implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: c1b64b9d32409d61284f21ca216417ece4767d1b
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553809"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="3634b-105">5. integrazione di ancoraggi spaziali di Azure in un'esperienza condivisa</span><span class="sxs-lookup"><span data-stu-id="3634b-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="3634b-106">In questa lezione si apprenderà come integrare Azure Spatial Anchors (ASA) nell'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="3634b-106">In this lesson, you'll learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="3634b-107">ASA consente a più dispositivi con percorso condiviso di avere un riferimento comune se l'ambiente fisico prevede l'ancoraggio di esperienze virtuali in modo che tutti i partecipanti vedano gli oggetti nella stessa posizione fisica.</span><span class="sxs-lookup"><span data-stu-id="3634b-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

## <a name="objectives"></a><span data-ttu-id="3634b-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="3634b-108">Objectives</span></span>

* <span data-ttu-id="3634b-109">Integrare ASA in un'esperienza condivisa per l'allineamento di più dispositivi.</span><span class="sxs-lookup"><span data-stu-id="3634b-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
* <span data-ttu-id="3634b-110">Informazioni sulle nozioni di base sul funzionamento di ASA nel contesto di un'esperienza condivisa locale.</span><span class="sxs-lookup"><span data-stu-id="3634b-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

## <a name="instructions"></a><span data-ttu-id="3634b-111">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="3634b-111">Instructions</span></span>

1. <span data-ttu-id="3634b-112">Selezionare la prefabbricazione TableAnchor sotto l'oggetto padre MixedRealityPlayspace ed eliminarla.</span><span class="sxs-lookup"><span data-stu-id="3634b-112">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. <span data-ttu-id="3634b-114">Nella visualizzazione del progetto passare a assets-> Resources-> prefabbricates e trascinare il prefabbricato TableAnchor sull'oggetto SharedPlayground per impostarlo come figlio.</span><span class="sxs-lookup"><span data-stu-id="3634b-114">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>

3. <span data-ttu-id="3634b-115">Espandere l'oggetto padre MixedRealityPlayspace, l'oggetto TableAnchor ed espandere anche l'oggetto Buttons.</span><span class="sxs-lookup"><span data-stu-id="3634b-115">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span>

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="3634b-117">A questo punto, nella gerarchia selezionare ShareAzureAnchorButton e spostare l'attenzione sul pannello Inspector.</span><span class="sxs-lookup"><span data-stu-id="3634b-117">Now in the hierarchy, select ShareAzureAnchorButton and move your attention to the Inspector panel.</span></span> <span data-ttu-id="3634b-118">Scorrere verso il basso fino al menu a discesa visualizzato nell'immagine seguente, selezionare AnchorModuleScript e fare clic su ShareAnchorNetwork ().</span><span class="sxs-lookup"><span data-stu-id="3634b-118">Scroll down to the drop-down menu shown in the image below, select AnchorModuleScript and click ShareAnchorNetwork().</span></span>

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="3634b-120">Selezionare GetAzureAnchorButton (vedere il passaggio 4) e riportare l'attenzione al pannello Inspector.</span><span class="sxs-lookup"><span data-stu-id="3634b-120">Select GetAzureAnchorButton (see Step 4) and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="3634b-121">Scorrere verso il basso fino al menu a discesa visualizzato nell'immagine seguente, selezionare AnchorModuleScript, fare clic su GetSharedAnchorNetwork () e quindi su Save (Salva).</span><span class="sxs-lookup"><span data-stu-id="3634b-121">Scroll down to the drop-down menu displayed in the image below, select AnchorModuleScript, click GetSharedAnchorNetwork(), and save.</span></span>

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="3634b-123">Ripetere il passaggio 4 per collegare la funzione StartAzureSession () a StartAzureSessionButton.</span><span class="sxs-lookup"><span data-stu-id="3634b-123">Repeat step 4 to hook up the StartAzureSession () function to the StartAzureSessionButton.</span></span>

7. <span data-ttu-id="3634b-124">Ripetere il passaggio 4 per collegare la funzione CreateAzureAnchor () a CreateAzureAnchorButton e verificare che l'oggetto TableAnchor sia assegnato al campo ' oggetto gioco ' del parametro della funzione.</span><span class="sxs-lookup"><span data-stu-id="3634b-124">Repeat step 4 to hook up the CreateAzureAnchor () function to the CreateAzureAnchorButton and verify that the TableAnchor object is assigned to the function's parameter 'Game Object' field.</span></span>

8. <span data-ttu-id="3634b-125">Seguire le istruzioni per la [connessione della scena alle risorse di Azure](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) per aggiungere le credenziali del servizio ancoraggi spaziali di Azure.</span><span class="sxs-lookup"><span data-stu-id="3634b-125">Follow the [Connect the scene to the Azure resource](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) instructions to add your Azure Spatial Anchors service credentials.</span></span>

9. <span data-ttu-id="3634b-126">Per testare il modulo di condivisione, fare clic sul pulsante "Avvia sessione di Azure ASA" che avvierà la sessione di ancoraggi spaziali di Azure e quindi creare l'ancoraggio di Azure facendo clic sul pulsante "Crea ancoraggio Azure".</span><span class="sxs-lookup"><span data-stu-id="3634b-126">To test the sharing module, click the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button.</span></span> <span data-ttu-id="3634b-127">Attendere che l'ancoraggio di Azure venga creato.</span><span class="sxs-lookup"><span data-stu-id="3634b-127">Wait for the azure anchor to get created.</span></span> <span data-ttu-id="3634b-128">Dopo aver creato l'ancoraggio di Azure, fare clic sul pulsante "Condividi Azure Anchor" per condividere l'ancoraggio Azure creato dal HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3634b-128">Once the azure anchor is created, click the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

10. <span data-ttu-id="3634b-129">Per ricevere l'ancoraggio Azure condiviso in un altro HoloLens, fare clic su "Avvia sessione di Azure ASA" per avviare e ottenere la sessione ASA corrente</span><span class="sxs-lookup"><span data-stu-id="3634b-129">To receive the shared azure anchor in another HoloLens, click the "Start Azure ASA Session" to start and get in to the current ASA session</span></span>

11. <span data-ttu-id="3634b-130">Fare clic sul pulsante "Get Azure Anchor" per ottenere l'ancoraggio Azure condiviso dall'altro HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3634b-130">Click the "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

## <a name="congratulations"></a><span data-ttu-id="3634b-131">Complimenti</span><span class="sxs-lookup"><span data-stu-id="3634b-131">Congratulations</span></span>

<span data-ttu-id="3634b-132">In questa lezione si è appreso come integrare i nuovi ancoraggi spaziali avanzati di Azure per allineare i dispositivi con percorso condiviso in un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="3634b-132">In this lesson, you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="3634b-133">Si conclude anche il modulo sharing.</span><span class="sxs-lookup"><span data-stu-id="3634b-133">This also concludes the Sharing Module.</span></span> <span data-ttu-id="3634b-134">Si è appreso come configurare un nuovo account Photon, integrare Photon e PUN in una nuova applicazione Unity, configurare avatar e oggetti condivisi e infine allineare più partecipanti usando ASA.</span><span class="sxs-lookup"><span data-stu-id="3634b-134">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configure avatars and shared objects, and finally align multiple participants using ASA.</span></span>

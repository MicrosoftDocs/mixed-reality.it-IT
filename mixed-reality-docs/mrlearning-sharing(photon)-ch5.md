---
title: Esercitazioni sulle funzionalità multiutente - 5. Integrazione di Ancoraggi nello spazio di Azure in un'esperienza condivisa
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7fb8cd03b2f3739037dee38786493bfd9012f6ce
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031684"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="07465-105">5. Integrazione di Ancoraggi nello spazio di Azure in un'esperienza condivisa</span><span class="sxs-lookup"><span data-stu-id="07465-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="07465-106">In questa lezione apprenderai come integrare Ancoraggi nello spazio di Azure nell'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="07465-106">In this lesson, you'll learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="07465-107">Questo servizio consente a più dispositivi con percorso condiviso di avere un riferimento comune se l'ambiente fisico prevede l'ancoraggio di esperienze virtuali in modo che tutti i partecipanti vedano gli oggetti nella stessa posizione fisica.</span><span class="sxs-lookup"><span data-stu-id="07465-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

## <a name="objectives"></a><span data-ttu-id="07465-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="07465-108">Objectives</span></span>

* <span data-ttu-id="07465-109">Integrare Ancoraggi nello spazio di Azure in un'esperienza condivisa per l'allineamento di più dispositivi.</span><span class="sxs-lookup"><span data-stu-id="07465-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
* <span data-ttu-id="07465-110">Apprendere le nozioni di base sul funzionamento di Ancoraggi nello spazio di Azure nel contesto di un'esperienza condivisa locale.</span><span class="sxs-lookup"><span data-stu-id="07465-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

## <a name="instructions"></a><span data-ttu-id="07465-111">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="07465-111">Instructions</span></span>

1. <span data-ttu-id="07465-112">Seleziona il prefab TableAnchor sotto l'oggetto padre MixedRealityPlayspace ed eliminalo.</span><span class="sxs-lookup"><span data-stu-id="07465-112">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. <span data-ttu-id="07465-114">Nella vista Project (Progetto) passa ad Assets (Asset)->Resources (Risorse)->Prefabs (Prefab) e trascina il prefab TableAnchor sull'oggetto SharedPlayground per farlo diventare un oggetto figlio.</span><span class="sxs-lookup"><span data-stu-id="07465-114">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>

3. <span data-ttu-id="07465-115">Espandi l'oggetto padre MixedRealityPlayspace, l'oggetto TableAnchor ed espandi anche l'oggetto Buttons.</span><span class="sxs-lookup"><span data-stu-id="07465-115">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span>

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="07465-117">A questo punto, nella gerarchia seleziona ShareAzureAnchorButton e concentra la tua attenzione sul pannello Inspector (Controllo).</span><span class="sxs-lookup"><span data-stu-id="07465-117">Now in the hierarchy, select ShareAzureAnchorButton and move your attention to the Inspector panel.</span></span> <span data-ttu-id="07465-118">Scorri verso il basso fino al menu a discesa visualizzato nell'immagine seguente, scegli AnchorModuleScript e fai clic su ShareAnchorNetwork().</span><span class="sxs-lookup"><span data-stu-id="07465-118">Scroll down to the drop-down menu shown in the image below, select AnchorModuleScript and click ShareAnchorNetwork().</span></span>

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="07465-120">Seleziona GetAzureAnchorButton (vedi il passaggio 4) e concentrati di nuovo sul pannello Inspector (Controllo).</span><span class="sxs-lookup"><span data-stu-id="07465-120">Select GetAzureAnchorButton (see Step 4) and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="07465-121">Scorri verso il basso fino al menu a discesa visualizzato nell'immagine seguente, scegli AnchorModuleScript, fai clic su GetSharedAnchorNetwork() ed effettua il salvataggio.</span><span class="sxs-lookup"><span data-stu-id="07465-121">Scroll down to the drop-down menu displayed in the image below, select AnchorModuleScript, click GetSharedAnchorNetwork(), and save.</span></span>

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="07465-123">Ripeti il passaggio 4 per collegare la funzione StartAzureSession () a StartAzureSessionButton.</span><span class="sxs-lookup"><span data-stu-id="07465-123">Repeat step 4 to hook up the StartAzureSession () function to the StartAzureSessionButton.</span></span>

7. <span data-ttu-id="07465-124">Ripeti il passaggio 4 per collegare la funzione CreateAzureAnchor () a CreateAzureAnchorButton e verifica che l'oggetto TableAnchor sia assegnato al campo "Game Object" (Oggetto Game) del parametro della funzione.</span><span class="sxs-lookup"><span data-stu-id="07465-124">Repeat step 4 to hook up the CreateAzureAnchor () function to the CreateAzureAnchorButton and verify that the TableAnchor object is assigned to the function's parameter 'Game Object' field.</span></span>

8. <span data-ttu-id="07465-125">Segui le istruzioni contenute in [Collegare la scena alla risorsa di Azure](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) per aggiungere le tue credenziali del servizio Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="07465-125">Follow the [Connect the scene to the Azure resource](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) instructions to add your Azure Spatial Anchors service credentials.</span></span>

9. <span data-ttu-id="07465-126">Per provare il modulo di condivisione, avvia la sessione facendo clic sul pulsante "Start Azure ASA Session" (Avvia sessione di Ancoraggi nello spazio di Azure) e quindi crea l'ancoraggio facendo clic sul pulsante "Create Azure Anchor" (Crea ancoraggio di Azure).</span><span class="sxs-lookup"><span data-stu-id="07465-126">To test the sharing module, click the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button.</span></span> <span data-ttu-id="07465-127">Attendi che l'ancoraggio di Azure venga creato.</span><span class="sxs-lookup"><span data-stu-id="07465-127">Wait for the azure anchor to get created.</span></span> <span data-ttu-id="07465-128">Dopo aver creato l'ancoraggio di Azure, fai clic sul pulsante "Share Azure Anchor" (Condividi ancoraggio di Azure) per condividere da HoloLens l'ancoraggio di Azure creato.</span><span class="sxs-lookup"><span data-stu-id="07465-128">Once the azure anchor is created, click the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

10. <span data-ttu-id="07465-129">Per ricevere l'ancoraggio di Azure condiviso in un altro HoloLens, fai clic su "Start Azure ASA Session" (Avvia sessione di Ancoraggi nello spazio di Azure) per avviare e accedere alla sessione corrente di Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="07465-129">To receive the shared azure anchor in another HoloLens, click the "Start Azure ASA Session" to start and get in to the current ASA session</span></span>

11. <span data-ttu-id="07465-130">Fai clic sul pulsante "Get Azure Anchor" (Ottieni ancoraggio di Azure) per ottenere dall'altro HoloLens l'ancoraggio di Azure condiviso.</span><span class="sxs-lookup"><span data-stu-id="07465-130">Click the "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

## <a name="congratulations"></a><span data-ttu-id="07465-131">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="07465-131">Congratulations</span></span>

<span data-ttu-id="07465-132">In questa lezione hai appreso come integrare il nuovo e potente servizio Ancoraggi nello spazio di Azure per allineare i dispositivi con percorso condiviso in un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="07465-132">In this lesson, you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="07465-133">Qui inoltre si conclude il modulo di condivisione.</span><span class="sxs-lookup"><span data-stu-id="07465-133">This also concludes the Sharing Module.</span></span> <span data-ttu-id="07465-134">Hai appreso come impostare un nuovo account Photon, integrare Photon e PUN in una nuova applicazione Unity, configurare avatar e oggetti condivisi e infine allineare più partecipanti con Ancoraggio nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="07465-134">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configure avatars and shared objects, and finally align multiple participants using ASA.</span></span>

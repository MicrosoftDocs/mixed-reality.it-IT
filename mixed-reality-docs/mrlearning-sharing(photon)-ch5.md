---
title: Modulo MR Learning sharing per HoloLens 2
description: Completare questo corso per apprendere come implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 1ae880208e79e2e045bd5e7298db260b7f0b2232
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293630"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="3746b-104">Ancoraggi spaziali e esperienze condivise di Azure</span><span class="sxs-lookup"><span data-stu-id="3746b-104">Azure Spatial Anchors and shared experiences</span></span>

<span data-ttu-id="3746b-105">In questa lezione viene illustrato come integrare Azure Spatial Anchors (ASA) nell'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="3746b-105">In this lesson, we learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="3746b-106">ASA consente a più dispositivi con percorso condiviso di avere un riferimento comune se l'ambiente fisico prevede l'ancoraggio di esperienze virtuali in modo che tutti i partecipanti vedano gli oggetti nella stessa posizione fisica.</span><span class="sxs-lookup"><span data-stu-id="3746b-106">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="3746b-107">Prima di procedere con questa lezione, è necessario completare il modulo ASA Learning, che riguarderà le nozioni di base di ASA, la creazione di account e risorse di Azure e altri blocchi di edifici fondamentali necessari prima di poter integrare ASA nell'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="3746b-107">Before proceeding with this lesson, we'll need to complete the ASA learning module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="3746b-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="3746b-108">Objectives:</span></span>

- <span data-ttu-id="3746b-109">Integrare ASA in un'esperienza condivisa per l'allineamento di più dispositivi.</span><span class="sxs-lookup"><span data-stu-id="3746b-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
- <span data-ttu-id="3746b-110">Informazioni sulle nozioni di base sul funzionamento di ASA nel contesto di un'esperienza condivisa locale.</span><span class="sxs-lookup"><span data-stu-id="3746b-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

### <a name="instructions"></a><span data-ttu-id="3746b-111">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="3746b-111">Instructions</span></span>

1. <span data-ttu-id="3746b-112">Salvare il progetto dalla lezione precedente (CTRL + S) e denominarlo "HLSharedProjectMainPart5. Unity" in modo che sia più facile da trovare quando è necessario.</span><span class="sxs-lookup"><span data-stu-id="3746b-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="3746b-113">Selezionare la prefabbricazione TableAnchor sotto l'oggetto padre MixedRealityPlayspace ed eliminarla.</span><span class="sxs-lookup"><span data-stu-id="3746b-113">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3.  <span data-ttu-id="3746b-115">Nella visualizzazione del progetto passare a assets-> Resources-> prefabbricates e trascinare il prefabbricato TableAnchor sull'oggetto SharedPlayground per impostarlo come figlio.</span><span class="sxs-lookup"><span data-stu-id="3746b-115">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="3746b-116">Espandere l'oggetto padre MixedRealityPlayspace, l'oggetto TableAnchor ed espandere anche l'oggetto Buttons.</span><span class="sxs-lookup"><span data-stu-id="3746b-116">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="3746b-118">A questo punto, nella gerarchia selezionare ShareAzureAnchorButton e spostare l'attenzione sul pannello inaspectr.</span><span class="sxs-lookup"><span data-stu-id="3746b-118">Now in the hierarchy, select ShareAzureAnchorButton, and move your attention to the Inaspector panel.</span></span> <span data-ttu-id="3746b-119">Scorrere verso il basso fino al menu a discesa visualizzato nell'immagine seguente e selezionare AnchorModuleScript e fare clic su ShareAnchorNetework ().</span><span class="sxs-lookup"><span data-stu-id="3746b-119">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript and click ShareAnchorNetework().</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="3746b-121">Selezionare GetAzureAnchorButton (vedere il passaggio 4) e riportare l'attenzione al pannello Inspector.</span><span class="sxs-lookup"><span data-stu-id="3746b-121">Select GetAzureAnchorButton (see Step 4), and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="3746b-122">Scorrere verso il basso fino al menu a discesa visualizzato nell'immagine seguente e selezionare AnchorModuleScript, quindi fare clic su GetSharedAnchorNetwork () e quindi su Salva.</span><span class="sxs-lookup"><span data-stu-id="3746b-122">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript, and click GetSharedAnchorNetwork(), and save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="3746b-124">Per testare il modulo di condivisione, fare clic sul pulsante "Avvia sessione di Azure ASA" che avvierà la sessione di ancoraggio spaziale di Azure e quindi creare l'ancoraggio di Azure facendo clic sul pulsante "Crea ancoraggio Azure" e attendere qualche minuto per la creazione dell'ancoraggio di Azure.</span><span class="sxs-lookup"><span data-stu-id="3746b-124">To test the sharing module, click on the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button and wait for sometime for the azure anchor to get created.</span></span> <span data-ttu-id="3746b-125">Dopo aver creato l'ancoraggio di Azure, fare clic sul pulsante "Condividi Azure Anchor" per condividere l'ancoraggio Azure creato dal HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3746b-125">Once the azure anchor is created then click on the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

7. <span data-ttu-id="3746b-126">Per ricevere l'ancoraggio Azure condiviso in un altro HoloLens, fare clic su "Avvia sessione di Azure ASA" per avviare e ottenere la sessione ASA corrente e fare clic sul pulsante "Ottieni ancoraggio di Azure" per ottenere l'ancoraggio Azure condiviso dall'altro HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3746b-126">To recieve the shared azure anchor in another HoloLens, click on the "Start Azure ASA Session" to start and get in to the current ASA session and click on "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

   > <span data-ttu-id="3746b-127">Nota: Tutti i dettagli delle azioni corrispondenti sui singoli pulsanti verranno visualizzati nella finestra di debug.</span><span class="sxs-lookup"><span data-stu-id="3746b-127">Note: All details of the corresponding actions on the individual buttons will be displayed in the debug window.</span></span>

## <a name="congratulations"></a><span data-ttu-id="3746b-128">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="3746b-128">Congratulations</span></span>

<span data-ttu-id="3746b-129">In questa lezione si è appreso come integrare i nuovi ancoraggi spaziali di Azure per allineare i dispositivi con percorso condiviso in un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="3746b-129">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="3746b-130">Questa lezione conclude anche il modulo sharing.</span><span class="sxs-lookup"><span data-stu-id="3746b-130">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="3746b-131">Si è appreso come configurare un nuovo account Photon, integrare Photon e PUN in una nuova applicazione Unity, configurare gli avatar e gli oggetti condivisi e infine allineare più partecipanti usando ASA.</span><span class="sxs-lookup"><span data-stu-id="3746b-131">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 

